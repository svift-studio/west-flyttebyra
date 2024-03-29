<svelte:head>
    <title>Kontakt Oss - West Flyttebyrå</title>
    <meta name="description" content="Vi er et flyttebyrå i Oslo med 30 års erfaring og mange gode kunde referanser. Ta kontakt med oss idag for å få tilbud på din neste flytting i Oslo.">
</svelte:head>

<script>
    import { browser } from '$app/environment';
    import emailjs from '@emailjs/browser';
    import { onMount } from "svelte";
    import { goto } from '$app/navigation';

    let inNavn = '';
    let inEpost = '';
    let inPrefix = "+47";
    let inMobilnummer = '';
    let inMelding = '';

    let formBtn;
    let sending = false;
    let formFilled = false;

    onMount(() => {
        emailjs.init({
            publicKey: import.meta.env.VITE_EJS_PKEY,
        });
    })

    $: if (browser ) {
        formFilled = 
            (inNavn.length>3) && 
            (inEpost.length>3 && inEpost.includes('@') && inEpost.includes('.')) &&
            !sending
    }

    function sendEmail() {
        if (!formFilled) return;
        sending = true;
        formBtn.textContent = "Sender..."
        emailjs.send("service_3yktczh","kontakt-oss",{
            navn: inNavn,
            epost: inEpost,
            prefix: inPrefix,
            mobilnummer: inMobilnummer,
            melding: inMelding
        }).then(() => {
            formBtn.textContent = "Suksess!";
            sending = false;
            goto('/suksess');
        }, (error) => {
            formBtn.textContent = "Error :(";
            console.error('Svift | ', error);
            sending = false;
        });
    }
</script>

<section class="hero">
    <div class="hero-text">
        <h1 class="xxl we-b">Kontakt oss</h1>
        <p>Trenger du hjelp eller har spørsmål angående din kommende flytting? Vår dedikerte kundeservice er her for å hjelpe deg. Kontakt oss i dag for å få mer informasjon.</p>
    </div>
    <div class="hero-content">
        <div class="hero-item">
            <img src="/icons/phone_inverted.svg" alt="Phone">
            <p class="xl we-r">Telefonnummer</p>
            <a class="op-h" href="tel:+4748905000">+47 489 05 000</a>
        </div>
        <div class="hero-item">
            <img src="/icons/mail_inverted.svg" alt="Mail letter">
            <p class="xl we-r">E-post</p>
            <a class="op-h" href="mailto:post@westflyttebyra.no">post@westflyttebyra.no</a>
        </div>
        <div class="hero-item">
            <img src="/icons/pin.svg" alt="Address pin">
            <p class="xl we-r">Adresse</p>
            <p class="op-h">Ole Deviks vei 35, 0668 Oslo</p>
        </div>
    </div>
</section>
<section class="form">
    <div class="form-text">
        <h2 class="xxl we-m">Vil du heller sende oss en melding?</h2>
        <p>Vi svarer vanligvis samme dag.</p>
    </div>
    <form>
        <h2 class="m we-m">Kontaktskjema</h2>
        <div class="divider fw"></div>
        <div class="form-item">
            <label for="name">Navn*</label>
            <input required bind:value="{inNavn}" type="text" id="name" placeholder="Ole Gunnarsen">
        </div>
        <div class="form-item">
            <label for="mail">E-post*</label>
            <input required bind:value="{inEpost}" type="email" id="mail" placeholder="ole@mail.com">
        </div>
        <div class="form-item">
            <label for="number">Mobilnummer</label>
            <div>
                <input bind:value="{inPrefix}" maxlength="4" type="text" placeholder="+47">
                <input bind:value="{inMobilnummer}" type="number" id="number" placeholder="000 00 000">
            </div>
        </div>
        <div class="form-item">
            <label for="melding">Melding</label>
            <textarea bind:value="{inMelding}" name="melding" id="melding" placeholder="Skriv din melding her"></textarea>
        </div>
        <button bind:this="{formBtn}" disabled="{!formFilled}" type="submit" on:click="{sendEmail}" class="inverted">Send</button>
        <p class="s op-m">Ved å sende inn skjemaet godtar du <u><a href="/personvern">personvernserklæringen.</a></u></p>
    </form>
</section>
<div class="img-divider">
    <img src="/happy.webp" alt="West flyttbyrå hjelper deg med flytting i oslo området">
</div>


<style>
    .hero {
        padding: var(--gap-small) 20px;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        gap: var(--gap-medium);
        background: var(--secondary-color);
        -webkit-box-align: center;
            -ms-flex-align: center;
                align-items: center;
    }

    .hero-text {
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        gap: 20px;
        text-align: center;
        max-width: 550px;
        color: var(--primary-color);
    }

    .hero-content {
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        -webkit-box-align: center;
            -ms-flex-align: center;
                align-items: center;
        gap: 22px;
        width: 100%;
        max-width: 1000px;
    }

    .hero-item {
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-align: center;
            -ms-flex-align: center;
                align-items: center;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        gap: 20px;
        padding: 20px;
        background: var(--background);
        border-radius: 20px;
        
        width: 100%;
        max-width: 450px;
        text-align: center;
    }

    .form {
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        padding: var(--gap-medium) 20px;
        gap: var(--gap-small);
        background: var(--secondary-color);
        -webkit-box-align: center;
            -ms-flex-align: center;
                align-items: center;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
    }

    .form-text {
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        gap: 24px;
        text-align: center;
        -webkit-box-align: center;
            -ms-flex-align: center;
                align-items: center;
        color: var(--primary-color);
        max-width: 450px;
    }

    form {
        width: 100%;
        max-width: 480px;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        gap: 20px;
    }

    form p {
        text-align: center;
    }
    
    .img-divider {
        background: var(--secondary-color)
    }

    .img-divider img {
        width: 100%;
        -o-object-fit: cover;
           object-fit: cover;
        -o-object-position: center;
           object-position: center;
        max-height: 500px;
    }

    @media screen and (min-width: 870px) {
        .form {
            padding: var(--gap-large) 24px;
            gap: var(--gap-medium);
        }        

        .hero {
            padding: var(--gap-large) 24px;
        }

        .hero h1 {
            font-size: var(--text-display);
        }

        .hero-content {
            -webkit-box-orient: horizontal;
            -webkit-box-direction: normal;
                -ms-flex-direction: row;
                    flex-direction: row;
        }

        .hero-item {
            max-width: unset;
        }
    }
</style>
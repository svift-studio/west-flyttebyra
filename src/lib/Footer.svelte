<script>
    import { page } from '$app/stores';

    function scrollUp() {
        window.scroll({
            top: document.querySelector('main'),
            behavior: 'smooth'
        });
    }
</script>

<footer class:special="{$page.url.pathname === '/flyttekalkulator'}">
    <div class="logo">
        <a href="/"><img class="icon" src="/logo.svg" alt="West Icon"></a>
    </div>
    
    <div class="container">
        <div class="items">
            <div class="item">
                <p class="m we-b">West Flyttebyrå</p>
                <a class="m" href="/">Hjem</a>
                <a class="m" href="/flyttekalkulator">Kalkulator</a>
                <a class="m" href="/kontakt-oss">Kontakt oss</a>
                <a class="m" href="/om-oss">Om oss</a>
                <a class="m" href="/personvern">Personvern</a>
            </div>
            <div class="item">
                <p class="m we-b">Kontakt</p>
                <a class="m" href="tel:+4748905000">+47 489 05 000</a>
                <a class="m" href="mailto:post@westflyttebyra.no">post@westflyttebyra.no</a>
                <p class="m">Ole Deviks vei 35,<br/> 0668 Oslo</p>
                <p class="m">Org nr 918 580 999</p>
            </div>
            <div class="item">
                <p class="m we-b">Sosialt</p>
                <a class="m" href="https://www.facebook.com/Westflyttebyra.no" target="_blank">Facebook</a>
                <a class="m" href="https://www.instagram.com/westflyttebyra" target="_blank">Instagram</a>
            </div>
        </div>
        <button on:click|preventDefault={scrollUp} class="m up btn-unset">Tilbake til toppen <img class="arrow" src="/arrow.svg" alt="Arrow up"></button>
    </div>
    <div class="bottom">
        <p class="m">©2024 West Flyttebyrå AS</p>
        <p class="m">Nettside av <span><a href="http://rosholm.studio" class="underline">Røsholm</a>®</span></p>
    </div>
</footer>

<style>
    footer {
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
        padding: var(--gap-large) 20px 40px 20px;
        background: var(--secondary-color);
        color: var(--primary-color);
    }

    footer.special {
        padding-bottom: calc(40px + var(--calc-footer));
    }

    .container {
        width: 100%;
        max-width: 1000px;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        -webkit-box-pack: justify;
            -ms-flex-pack: justify;
                justify-content: space-between;
        gap: var(--gap-medium);
        padding: var(--gap-medium) 0 var(--gap-small) 0;
    }

    .items {
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        gap: var(--gap-medium);
    }

    .logo {
        width: 100%;
        max-width: 1000px;
    }

    .icon {
        width: 57px;
    }

    .arrow {
        height: 20px;
        width: 20px;
    }

    .item {
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        gap: 8px;
    }

    .up {
        height: -webkit-fit-content;
        height: -moz-fit-content;
        height: fit-content;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-align: center;
            -ms-flex-align: center;
                align-items: center;
    }

    .bottom {
        width: 100%;
        max-width: 1000px;
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-orient: vertical;
        -webkit-box-direction: normal;
            -ms-flex-direction: column;
                flex-direction: column;
        padding-top: var(--gap-small);
        gap: 8px;
        border-top: 1px solid var(--border-light);
    }

    @media screen and (min-width: 550px) {
        .items {
            -webkit-box-orient: horizontal;
            -webkit-box-direction: normal;
                -ms-flex-direction: row;
                    flex-direction: row;
        }

        .bottom {
            -webkit-box-orient: horizontal;
            -webkit-box-direction: normal;
                -ms-flex-direction: row;
                    flex-direction: row;
            -webkit-box-pack: justify;
                -ms-flex-pack: justify;
                    justify-content: space-between;
        }
    }

    @media screen and (min-width: 830px) {
        .container {
            -webkit-box-orient: horizontal;
            -webkit-box-direction: normal;
                -ms-flex-direction: row;
                    flex-direction: row;
            -webkit-box-pack: justify;
                -ms-flex-pack: justify;
                    justify-content: space-between;
            padding: var(--gap-large) 0;
        }

        .items {
            gap: 87px;
        }
    }

    .underline {
        text-decoration: underline;
    }
</style>
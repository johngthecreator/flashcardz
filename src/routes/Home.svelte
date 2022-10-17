<script>
let hero = './herobanner.svg'
let cards = './cards.svg'
let explain = './explanation.svg'
import {Link} from "svelte-routing";
</script>
<main>
    <div style="display: flex; flex-direction: column; align-items: center;">
        <div class="textWrapper">
            <img src={cards} alt="cards" />
            <div class="heroContentWrapper">
                <h1 style="text-align: center;">the fastest way to make flashcards</h1>
                <Link class="goButton" to="flashcards">Get Started</Link>
            </div>
        </div>
        <h1>How does it work?</h1>
        <div class="textWrapper">
            <h2>Comet automatically pulls all the information it needs right from your notes. Just separate the term and definition with a colon and let Comet do the rest. While generating, each new line becomes a separate card.</h2>
            <img src={explain} alt="explainer" />
        </div>
        <h1>When should I use Comet?</h1>
        <div class="textWrapper">
            <h2>Use Comet whenever you want! We all know the worst part about studying flashcards is making them, the main purpose of Comet is to provide a quick and easy way to make flashcards. Comet lets you skip the painful process of making cards and lets you get right to memorizing! </h2>
        </div>

        
    </div>
</main>
<footer>
  <p>CometNotes Copyright 2022</p>
</footer>
<style>
    .textWrapper{
        display: flex; 
        flex-direction: row; 
        align-items: center;
        line-height: 30px;
        padding: 25px;
    }
    img{
        width: 50%; 
        height: auto;
    }
    .heroContentWrapper{
        display: grid; 
        justify-items: center;
    }
    .goButton{
        width: auto; 
        color: white; 
        padding: 15px;
        border-radius: 10px;
        align-items: center; 
        background-color: #256EFF; 
        border: 2px solid #256EFF ;
        transition: .3s;
    }
    .goButton:hover{
        background-color: white;
        border: 2px solid #256EFF ;
        color: #256EFF; 
    }
    footer{
    background-color: #256EFF;
    overflow: hidden;
    padding: 5px;
    color: white;
    font-weight: 600;
    }
    @media only screen and (max-width: 768px){
        .textWrapper{
            flex-direction: column;
            justify-content: center;
        }
        img{
            width: 100%;
        }
        .textWrapper{
            text-align: center;
        }
    }
    
</style>

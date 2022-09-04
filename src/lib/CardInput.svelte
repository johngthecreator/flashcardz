<script>
    import {cardList} from "../stores.js"
    let emptyField;
    let notes = '';
    function addNotes(){
        let cardData = notes.split("\n");
        cardData.forEach((card)=>{
            $cardList = [...$cardList, {
                item: card
            }]
        })
        localStorage.setItem('cards', JSON.stringify($cardList))
        emptyField.value = '';
    }
    function clearNotes(){
        cardList.set([]);
        localStorage.setItem('cards', JSON.stringify($cardList))
    }
</script>
<div class="cardInput">
    <textarea bind:this={emptyField} bind:value={notes}></textarea>
    <div class="buttonWrapper">
        <button class="goButton" on:click={addNotes}>
            Make Flashcards
        </button>
        <button class="clearButton"on:click={clearNotes}>
            Clear
        </button>
    </div>
</div>

<style>
    textarea{
        resize:none;
        width:300px;
        height: 100px;
        border-radius: 10px;
        padding: 10px;
    }
    .cardInput{
        display: flex;   
        flex-direction: row;
        gap: 10px;
        justify-content: center;
        padding: 20px;
    }
    .buttonWrapper{
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
    .goButton{
        font-weight: 700;
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
        color: white;
        border: 2px solid rgb(67, 164, 67) ;
        background-color: rgb(67, 164, 67) ;
    }
    .clearButton{
        font-weight: 700;
        padding: 15px;
        border-radius: 10px;
        background-color: white;
        border: 2px solid #256EFF ;
        color: #256EFF; 
        transition: .3s;
    }
    .clearButton:hover{
        color: white;
        background-color: rgb(255, 123, 123);
        border: 2px solid rgb(255, 123, 123);
    }
    @media only screen and (max-width: 768px) {
        .cardInput{
            flex-direction: column;
        }
        .buttonWrapper{
            gap: 10px;
        }
    }
</style>
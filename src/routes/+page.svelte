<script lang="ts">
    
    let mode: number;
    let gameBegin: boolean = true;

    function cakeWalk(){
        mode=5;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    function easy(){
        mode=8;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    function normal(){
        mode=12;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    function hard(){
        mode=18;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    function veryHard(){
        mode=25;
        gameBegin = false;
        bombNumbers=getRandomNumbers();
        replay();
    }
    
    class Button {
        buttonNum: number;
        buttonClicked: boolean;
        borderBombs: number;

        constructor(num: number){
            this.buttonNum=num;
            this.buttonClicked=false;
            this.borderBombs=0;
        }
        
    }
    let gridButtons: Button[] = [];

    for (let i = 0; i < 64; i++) {
        gridButtons[i] = new Button(i);
    }

    let bombClicked = false;
    let buttonsClicked = 0;
    let gameWon = false;

    function getRandomNumbers() {
        let randomNumbers: number[] = [];

        while (randomNumbers.length < mode) {
            let randomNumber = Math.floor(Math.random() * 64);

            if (!randomNumbers.includes(randomNumber)) {
                randomNumbers.push(randomNumber);
            }
        }

        return randomNumbers;
    }

    let bombNumbers = getRandomNumbers();
    
    let disabledButtons: number[] = [];

    function handleClick(button: Button) {
        gridButtons[button.buttonNum].buttonClicked = true;
        if(disabledButtons.includes(button.buttonNum)){
            let nothing = 1;
        } else {
                if (bombNumbers.includes(button.buttonNum)) {
                    bombClicked = true;
                    disabledButtons = bombNumbers.slice();
                    throw "exit";
                }
                buttonsClicked++
                if(buttonsClicked == 64-mode){
                    gameWon = true;
                }
                disabledButtons.push(button.buttonNum);
                switch (button.buttonNum) {
                    case 16:
                    case 8:
                    case 24:
                    case 32:
                    case 40:
                    case 48:

                        if(bombNumbers.includes(button.buttonNum+1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;
            
                    case 1:
                    case 2:
                    case 3:
                    case 4:
                    case 5:
                    case 6:

                        if(bombNumbers.includes(button.buttonNum-1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;
                
                    case 57:
                    case 58:
                    case 59:
                    case 60:
                    case 61:
                    case 62:

                        if(bombNumbers.includes(button.buttonNum-1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    case 15:
                    case 23:
                    case 31:
                    case 39:
                    case 47:
                    case 55:

                        if(bombNumbers.includes(button.buttonNum-1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    case 0:

                        if(bombNumbers.includes(1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;
                    case 7:

                        if(bombNumbers.includes(6)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(15)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(14)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    case 56:
                
                        if(bombNumbers.includes(49)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(48)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(57)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    case 63:

                        if(bombNumbers.includes(62)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(54)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(55)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;

                    default:
                        if(bombNumbers.includes(button.buttonNum-1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+1)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+8)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+9)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum-7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        if(bombNumbers.includes(button.buttonNum+7)){
                            button.borderBombs = button.borderBombs + 1
                        }
                        break;
            }
        }
    }
    
    function replay() {
        for(let i: number = 0; i < gridButtons.length; i++) {
            gridButtons[i] = new Button(i);
            bombNumbers = getRandomNumbers();
            disabledButtons = [];
            bombClicked = false;
            buttonsClicked = 0;
            gameWon = false;
        }
    }
</script>

<h1>​</h1>
<h1>​</h1>
<h1>​</h1>
<h1>​</h1>

<div class="flex justify-center align-items: center">
    <div class="grid grid-cols-8 gap-2 w-fit">
        {#each gridButtons as num}
            {#if bombClicked || gameWon}
                {#if bombNumbers.includes(num.buttonNum) || num.buttonNum == bombNumbers[num.buttonNum]}
                    <button class="bg-red-500 w-16 h-16 max-sm:w-8 max-sm:h-8"> 💣 </button>
                {:else if num.buttonClicked}
                    <button class="bg-slate-900 text-blue-600 w-16 h-16 max-sm:w-8 max-sm:h-8"
                        on:click={() => handleClick(num)}> 
                        {num.borderBombs}
                    </button>
                {:else}
                    <button class="bg-orange-500 w-16 h-16 max-sm:w-8 max-sm:h-8"> 
                    </button>
                {/if}
            {:else if num.buttonClicked}
                <button class="bg-slate-900 text-blue-600 w-16 h-16 max-sm:w-8 max-sm:h-8"
                    on:click={() => handleClick(num)}> 
                    {num.borderBombs}
                </button>
            {:else}
                <button class="bg-orange-500 w-16 h-16 max-sm:w-8 max-sm:h-8"
                    on:click={() => handleClick(num)}> 
                </button>
            {/if}
        {/each}
    </div>
</div>

{#if bombClicked}
    <p class="message-overlay">You Lost</p>
    <button class="messageButton" on:click={replay}>Retry</button>
{/if}

{#if gameWon}
    <p class="message-overlayWin">You Won</p>
    <button class="messageButton" on:click={replay}>Replay</button>
{/if}

{#if gameBegin}
    <button class="moretop" on:click={cakeWalk}>Cakewalk</button>
    <button class="top" on:click={easy}>Easy</button>
    <button class="upMid" on:click={normal}>Normal</button>
    <button class="downMid" on:click={hard}>Hard</button>
    <button class="bottom" on:click={veryHard}>Very Hard</button>
{/if}

<h1>​</h1>
<h1>​</h1>
<h1>​</h1>
<h1>​</h1>

<style>
    .message-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 3rem;
        z-index: 998;
    }
    .message-overlayWin {
        opacity: 0.6;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: aliceblue;
        display: flex;
        justify-content: center;
        align-items: center;
        color: darkorange;
        font-size: 3rem;
        z-index: 998;
    }
    .messageButton {
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 25%;
        background: rgba(0, 0, 0, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 1.5rem;
        z-index: 999;
    }
    .moretop {
        opacity: 0.94;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 20%;
        background: aliceblue;
        display: block;
        justify-content: center;
        align-items: center;
        color: blue;
        font-size: 1.5rem;
        z-index: 999;
    }
    .top {
        opacity: 0.94;
        position: fixed;
        top: 20%;
        left: 0;
        width: 100%;
        height: 25%;
        background: greenyellow;
        display: block;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 1.5rem;
        z-index: 999;
    }
    .upMid {
        opacity: 0.94;
        position: fixed;
        top: 40%;
        left: 0;
        width: 100%;
        height: 20%;
        background: darkblue;
        display: block;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 1.5rem;
        z-index: 999;
    }
    .downMid {
        position: fixed;
        top: 60%;
        opacity: 0.94;
        left: 0;
        width: 100%;
        height: 20%;
        background: darkred;
        display: block;
        justify-content: center;
        align-items: center;
        color: darkviolet;
        font-size: 1.5rem;
        z-index: 999;
    }
    .bottom {
        position: fixed;
        bottom: 0;
        left: 0;
        width: 100%;
        opacity: 0.94;
        height: 20%;
        background: black;
        display: block;
        justify-content: center;
        align-items: center;
        color: white;
        font-size: 1.5rem;
        z-index: 999;
    }
</style>
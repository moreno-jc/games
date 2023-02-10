<script>
	// @ts-nocheck

	//opciones

	let piedra = '../img/piedra.jpg'; //0
	let papel = '../img/papel.jpg'; //1
	let tijera = '../img/tijera.jpg'; //2
	let signo = '../img/signo.png';

	let flagGame = false;
	let selectionuser = '';
	let valMachine = '';
	let nameValeMachine = '';
	let numberUser;
	let resultuserImgUser = signo;
	let resultuserImgMachine = signo;
	let resulFinal = '';

	//conteo
	let v = 0;
	let d = 0;
	let e = 0;

	function Game(valPlayer) {
		valMachine = Math.floor(Math.random() * 3);
		console.log('user valMachine', valMachine);
		if (valMachine === valPlayer) {

			switch (valMachine) {
				case 0:
					nameValeMachine = 'Piedra';
					resultuserImgMachine = piedra;
					break;
				case 1:
					nameValeMachine = 'Papel';
					resultuserImgMachine = papel;
					break;
				case 2:
					nameValeMachine = 'Tijera';
					resultuserImgMachine = tijera;
					break;
                    
			}

			resulFinal = 'Empate';
            e = e+1
			return 0;
		} else if (valMachine == 0) {
			nameValeMachine = 'Piedra';
			resultuserImgMachine = piedra;

			//piedra
			if (valPlayer == 1) {
				//papel
				resulFinal = 'Gano Player1';
                v = v+1
                if (v==3){
                    alert('Gano Player1')
                }
			} else {
				//tijera
				resulFinal = 'Gano Machine';
                d = d+1
                if (d==3){
                    alert('Gano Machine')
                }
			}
		} else if (valMachine == 1) {
			nameValeMachine = 'Papel';
			resultuserImgMachine = papel;
			//papel
			if (valPlayer == 0) {
				//piedra
				resulFinal = 'Gano Machine';
                d = d+1
                if (d==3){
                    alert('Gano Machine')
			} 
            }
            else {
				//tijera
				resulFinal = 'Gano Player1';
                v = v+1
                if (v==3){
                    alert('Gano Player1')
			} 
			}
		} else if (valMachine == 2) {
			nameValeMachine = 'Tijera';
			resultuserImgMachine = tijera;

			//tijera
			if (valPlayer == 0) {
				//piedra
				resulFinal = 'Gano Player1';
                v = v+1
                if (v==3){
                    alert('Gano Player1')
			}
            }   
            else {
				//papel
				resulFinal = 'Gano Machine';
                d = d+1
                if (d==3){
                    alert('Gano Machine')
			} 
			}
		}
	}

	function handleClick(val) {
		selectionuser = val;
		console.log('user val', val);

		if (val == 'Piedra') {
			resultuserImgUser = piedra;
			numberUser = 0;
		}
		if (val == 'Papel') {
			resultuserImgUser = papel;
			numberUser = 1;
		}
		if (val == 'Tijera') {
			resultuserImgUser = tijera;
			numberUser = 2;
		}
		Game(numberUser);
		flagGame = true;
	}

	//aqui va la funcion xd
</script>

<div class="container-fluid text-center mainContainer">
	<div class="row ">
		<div class="col-10 mt-5 mb-5">
			<h1 class="mt-5 mb-5 titulo">JUGUEMOS PIEDRA, PAPEL O TIJERA</h1>
			<div class="mt-5 opciones">
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<img on:click={() => handleClick('Piedra')} class="opc" src={piedra} alt="piedra" />
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<img on:click={() => handleClick('Papel')} class="opc" src={papel} alt="papel" />
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<img on:click={() => handleClick('Tijera')} class="opc" src={tijera} alt="tijera" />
			</div>
			<div class="row resultado">
				<div class="col-5">
					<h4 class="jugadores">You</h4>
					<h5>{selectionuser}</h5>
					<img class="ResulMachine" src={resultuserImgUser} alt="signo" />
				</div>

				<div class="col-2">
					<h2 class="letrero">VS</h2>
				</div>
				<div class="col-5">
					<h4 class="jugadores">Machine</h4>
					<!-- svelte-ignore missing-declaration -->
					<h5>{nameValeMachine}</h5>
					<img class="ResulMachine" src={resultuserImgMachine} alt="signo" />
				</div>
			</div>
		</div>
		<div class="col-2 mt-5 mb-5">
			<div class="conteo">
				<p class="mt-3">Victoria: {v}</p>
				<p class="mt-4 mb-3">Derrota: {d}</p>
				<p class="mt-4 mb-5">Empates {e}</p>
			</div>
			{#if flagGame}
				<p class="center">{resulFinal}</p>
			{/if}
		</div>
	</div>
</div>

<style>
	.titulo {
		font-size: 55px;
		text-align: center;
	}
	.mainContainer {
		background: -webkit-linear-gradient(90deg, #1b97b1 10%, #1b97b1 90%);
		background: -moz-linear-gradient(90deg, #9f5794 10%, #8cc8ac 90%);
		background: -ms-linear-gradient(90deg, #8cc8ac 10%, #9f5794 90%);
		background: -o-linear-gradient(90deg, #9f5794 10%, #8cc8ac 90%);
		background: linear-gradient(90deg, #9f5794 10%, #1b97b1 90%);
		font-family: 'Prompt', sans-serif;
	}
	.opciones {
		margin-top: 10%;
	}
	.jugadores {
		font-size: xx-large;
	}
	.letrero {
		margin-top: 30%;
		display: inline-block;
		-webkit-box-sizing: border-box;
		-moz-box-sizing: border-box;
		box-sizing: border-box;
		padding: 10px;
		border: none;
		font-family: 'Prompt', sans-serif;
		font-size: 200px;
		color: #d5a513;
		text-decoration: normal;
		text-align: center;
		-o-text-overflow: clip;
		text-overflow: clip;
		white-space: pre;
		text-shadow: 0 0 10px rgba(255, 255, 255, 1), 0 0 20px rgba(255, 255, 255, 1),
			0 0 30px rgba(255, 255, 255, 1), 0 0 40px #d5a513, 0 0 70px #d5a513, 0 0 80px #d5a513,
			0 0 100px #d5a513;
		-webkit-transition: all 200ms cubic-bezier(0.42, 0, 0.58, 1);
		-moz-transition: all 200ms cubic-bezier(0.42, 0, 0.58, 1);
		-o-transition: all 200ms cubic-bezier(0.42, 0, 0.58, 1);
		transition: all 200ms cubic-bezier(0.42, 0, 0.58, 1);
	}
	.letrero:hover {
		color: #d0487c;
		text-shadow: 0 0 10px rgba(255, 255, 255, 1), 0 0 20px rgba(255, 255, 255, 1),
			0 0 30px rgba(255, 255, 255, 1), 0 0 40px #9f5794, 0 0 70px #9f5794, 0 0 80px #9f5794,
			0 0 100px #9f5794;
	}
	.resultado {
		margin-top: 5%;
		margin-bottom: 10%;
	}
	.ResulMachine {
		width: 400px;
		height: 450px;
		border-radius: 70px;
	}
	.opc {
		margin-left: 5%;
		border-radius: 30px;
	}
	.conteo {
		font-size: x-large;
		margin-top: 50%;
		width: 200px;
		height: 200px;
		background-color: rgba(255, 221, 244, 0.09);
		border: rgb(249, 249, 249) solid 3.5px;
		border-radius: 30px;
	}
</style>

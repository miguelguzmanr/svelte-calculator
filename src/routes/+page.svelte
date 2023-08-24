<script>
	let screen = "";
	let operand, operator, result;

	const addInput = (s) => () => (screen += s);
	const clearInput = () => (screen = "");

	function setOperator(s) {
		operator = s;
		operand = Number(screen);
		clearInput();
	}

	function equal() {
		let currentOperand = Number(screen);

		if (operator === "+") result = operand + currentOperand;
		else if (operator === "-") result = operand - currentOperand;
		else if (operator === "*") result = operand * currentOperand;
		else if (operator === "/") result = operand / currentOperand;

		screen = result.toString();
	}
</script>

<div class="calculator">
	<div class="screen">{screen}</div>
	<div class="buttons">
		<button on:click={addInput(7)}>7</button>
		<button on:click={addInput(8)}>8</button>
		<button on:click={addInput(9)}>9</button>
		<button on:click={() => setOperator("+")} class="operator"> +</button>

		<button on:click={addInput(4)}>4</button>
		<button on:click={addInput(5)}>5</button>
		<button on:click={addInput(6)}>6</button>
		<button on:click={() => setOperator("-")} class="operator"> -</button>

		<button on:click={addInput(1)}>1</button>
		<button on:click={addInput(2)}>2</button>
		<button on:click={addInput(3)}>3</button>
		<button on:click={() => setOperator("*")} class="operator">
			&times;</button
		>

		<button on:click={addInput("00")} class="double-zero">00</button>
		<button on:click={addInput(0)}>0</button>
		<button on:click={addInput(".")}>.</button>
		<button on:click={() => setOperator("/")} class="operator">
			&divide;</button
		>

		<button on:click={clearInput} class="clear">
			<svg
				xmlns="http://www.w3.org/2000/svg"
				class="icon icon-tabler icon-tabler-trash"
				width="24"
				height="24"
				viewBox="0 0 24 24"
				stroke-width="2"
				stroke="currentColor"
				fill="none"
				stroke-linecap="round"
				stroke-linejoin="round"
			>
				<path stroke="none" d="M0 0h24v24H0z" fill="none" />
				<path d="M4 7l16 0" />
				<path d="M10 11l0 6" />
				<path d="M14 11l0 6" />
				<path d="M5 7l1 12a2 2 0 0 0 2 2h8a2 2 0 0 0 2 -2l1 -12" />
				<path d="M9 7v-3a1 1 0 0 1 1 -1h4a1 1 0 0 1 1 1v3" />
			</svg>
		</button>
		<button on:click={equal} class="equal"> =</button>
	</div>
</div>

<style>
	.calculator {
		margin: auto;
		display: flex;
		flex-direction: column;
		gap: 32px;
		background: #ffffff;
		border: 1px solid #cbd5e1;
		padding: 32px;
		box-shadow: 0px 8px 24px rgba(0, 0, 0, 0.1);
		border-radius: 16px;
		width: fit-content;
		font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
		font-style: normal;
	}

	.calculator .screen {
		display: flex;
		flex-direction: row;
		justify-content: end;
		align-items: center;

		background-color: #f8fafc;
		color: #94a3b8;
		border: 1px solid #cbd5e1;
		border-radius: 16px;
		width: 100%;
		height: 64px;
		font-family: inherit;
		font-style: inherit;
		font-weight: 400;
		font-size: 40px;
	}

	.calculator .buttons {
		display: grid;
		grid-template-columns: repeat(4, 64px);
		gap: 32px;
	}

	.calculator button {
		width: 100%;
		height: 64px;

		background: #ffffff;
		border-width: 1px 1px 4px 1px;
		border-style: solid;
		border-color: #cbd5e1;
		border-radius: 16px;
		color: #94a3b8;
		font-family: inherit;
		font-style: inherit;
		font-weight: 200;
		font-size: 32px;
	}

	.calculator button:hover {
		transition-duration: 0.2s;
		opacity: 0.75;
	}

	.calculator button.double-zero {
		font-size: 24px;
	}

	.calculator button.operator {
		background: #fb923c;
		border-width: 1px 1px 4px 1px;
		border-style: solid;
		border-color: #ea580c;
		border-radius: 16px;
		color: #ffffff;
	}

	.calculator button.clear {
		grid-column: span 2;
		background: #f87171;
		border-width: 1px 1px 4px 1px;
		border-style: solid;
		border-color: #dc2626;
		border-radius: 16px;
		color: #ffffff;
	}
	.calculator button.equal {
		grid-column: span 2;
		background: #38bdf8;
		border-width: 1px 1px 4px 1px;
		border-style: solid;
		border-color: #0284c7;
		border-radius: 16px;
		color: #ffffff;
	}
</style>

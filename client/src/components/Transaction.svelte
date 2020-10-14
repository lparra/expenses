<script>
import { slide } from 'svelte/transition';
export let transaction;
export let removeTransaction;
</script>

<div class="transactions-div">

    <div class="transaction">
        <span>{transaction.description}</span>
        <span>{new Date(transaction.date).toLocaleString()}</span>
    </div>

    <div class="amount" id="{transaction.value > 0 ? 'positive-amount' : 'negative-amount'}"
		transition:slide={{duration: 500 }}>
		<span>{transaction.value}</span>
        <button class="delete" on:click={()=> removeTransaction(transaction._id)} />
    </div>

</div>

<style>

.transactions-div {
	align-items: center;
	background-color: #1E2021;
	border-radius: 4px;
	display: flex;
	height: 100%;
	justify-content: space-between;
	margin: 0 auto;
	margin-bottom: 0.5rem;
	padding: 0.5rem;
	width: 100%;
}

.transactions-div span {
	margin: 0 16px;
}

.transaction {
	display: flex;
	flex-direction: column;
}

.transaction span:nth-of-type(2) {
	font-size: 12px;
}

#positive-amount span {
	color: #00F5C3
}

#negative-amount span {
	color: #EF2460
}

</style>
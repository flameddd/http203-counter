<script>
	const intervalTime = 1000;
	let seconds = 0;
	// ==== ex1 ====
	// let frame = () => {
	// 	seconds = seconds + 1;
	// }
	// const id = setInterval(frame, intervalTime)

	// ==== ex2 ====
	// const start = Date.now()
	// let frame = () => {
	// 	const elapsed = Date.now() - start

	// 	seconds = Math.floor(elapsed / intervalTime)
	// }
	// const id = setInterval(frame,intervalTime)

	// document.addEventListener('visibilitychange', () => {
	// 	if (document.hidden) {
	// 		clearInterval(id);
	// 	} else {
	// 		frame = setInterval(frame, intervalTime)
	// 	}
	// })


	// ==== ex3 ====
	// const start = Date.now()
	// function frame() {
	// 	const elapsed = Date.now() - start;
	// 	seconds = Math.floor(elapsed / intervalTime);
	// 	requestAnimationFrame(frame)
	// }
	// frame()

	// ==== ex4 ====
	// time of current frame when document been created
	// const start = document.timeline.currentTime;
	// function frame() {
	// 	const elapsed = document.timeline.currentTime - start;
	// 	seconds = Math.floor(elapsed / intervalTime);
		
	// 	document.body.animate(null, {
	// 		duration: intervalTime - elapsed % intervalTime
	// 	}).onfinish = frame
	// }
	// frame()

	// ==== ex5 ====
	// html + css keyframes

	// ==== ex6 ====
	// const start = document.timeline.currentTime;
	// function frame(time) {
	// 	const elapsed = time - start;
	// 	seconds = Math.floor(elapsed / intervalTime);
		
	// 	setTimeout(
	// 		() => requestAnimationFrame(frame),
	// 		intervalTime - elapsed % intervalTime
	// 	)
	// }
	// frame(start)

	// ==== ex7 ====
	const start = document.timeline.currentTime;
	function frame(time) {
		const elapsed = time - start;
		seconds = Math.round(elapsed / intervalTime);
		const targetNext = seconds + (intervalTime / 1000) * 1000 + start;
		
		setTimeout(
			() => requestAnimationFrame(frame),
			targetNext - performance.now()
		)
	}
	frame(start)


</script>

<main>
	<h1>{seconds}</h1>

	<!-- <div>
		<span class="first" />
		<span class="second" />
	</div> -->
</main>

<style>
	/* .first::before { 
		content:"0";
		animation: 100s linear infinite 5s backwards numbers;
	}
	.second::before {
		content:"0";
		animation: 10s linear infinite 0.5s backwards numbers;
	}

	@keyframes numbers {
		0% { content: '0';}
		10% { content: '1';}
		20% { content: '2';}
		30% { content: '3';}
		40% { content: '4';}
		50% { content: '5';}
		60% { content: '6';}
		70% { content: '7';}
		80% { content: '8';}
		90% { content: '9';}
	} */

</style>
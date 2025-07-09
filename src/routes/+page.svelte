<script>
	import { onMount } from 'svelte';

	let selectedUserType = 'arbeitnehmer';

	function handleUserTypeSelection(type) {
		selectedUserType = type;
		console.log('Selected user type:', type);
	}

	function handleRegistration() {
		console.log('Registration clicked');
	}

	onMount(() => {
		window.addEventListener('scroll', () => {
			const bar = document.getElementById('mobile-register-bar');
			const header = document.querySelector('.header');
			const isMobile = window.innerWidth <= 768;

			const scrollTop = window.scrollY;
			const barBtn = bar?.querySelector('.register-btn');
			const headerBtn = header?.querySelector('.register-btn');

			if (isMobile) {
				if (scrollTop > 0) {
					if (!headerBtn && barBtn) {
						const newBtn = barBtn.cloneNode(true);
						newBtn.onclick = handleRegistration;
						newBtn.style.marginLeft = '10px';
						header.appendChild(newBtn);
					}
					bar.style.display = 'none';
					if (barBtn) bar.removeChild(barBtn);
				} else {
					if (!barBtn && headerBtn) {
						const newBtn = headerBtn.cloneNode(true);
						newBtn.onclick = handleRegistration;
						bar.appendChild(newBtn);
						header.removeChild(headerBtn);
					}
					bar.style.display = 'flex';
				}
			} else {
				if (headerBtn) header.removeChild(headerBtn);
				bar.style.display = 'none';
			}
		});
	});
</script>

<main class="job-website">
	<header class="header">
		<div class="login-btn">Login</div>
	</header>
	<section class="hero">
		<!-- Hero Section -->
		<div class="content-container">
			<div class="hero-content">
				<h1 class="main-heading">
					Deine Job<br />
					website
				</h1>

				<button id="web-register-button" class="register-btn" on:click={handleRegistration}>
					Kostenlos Registrieren
				</button>
			</div>

			<!-- Handshake Illustration -->
			<div class="hero-illustration">
				<div class="step-illustration svg-circle-bg">
					<img id="asset0-img" src="/assets/asset0.svg" alt="Step 0 Illustration" />
				</div>
			</div>
			<div></div>
			<div id="mobile-register-bar">
				<button class="register-btn">Kostenlos Registrieren</button>
			</div>
		</div>
	</section>

	<section class="user-selection">
		<div class="user-buttons">
			<button
				class="user-btn {selectedUserType === 'arbeitnehmer' ? 'active' : ''}"
				on:click={() => handleUserTypeSelection('arbeitnehmer')}
			>
				Arbeitnehmer
			</button>
			<button
				class="user-btn {selectedUserType === 'arbeitgeber' ? 'active' : ''}"
				on:click={() => handleUserTypeSelection('arbeitgeber')}
			>
				Arbeitgeber
			</button>
			<button
				class="user-btn {selectedUserType === 'temporaerburo' ? 'active' : ''}"
				on:click={() => handleUserTypeSelection('temporaerburo')}
			>
				Temporärbüro
			</button>
		</div>
	</section>

	<section class="steps-intro">
		<h2 class="second-heading">
			Drei einfache Schritte<br />
			zu deinem neuen Job
		</h2>
	</section>

	<section class="steps">
		<div class="step">
			<div class="step-content-container">
				<div class="step-number">1.</div>
				<div class="step-content">
					<h3>Erstellen dein Lebenslauf</h3>
				</div>
			</div>
			<div class="step-illustration">
				<img src="/assets/asset1.svg" alt="Step 1 Illustration" />
			</div>
		</div>

		<div class="step">
			<svg
				class="wave-shape"
				viewBox="0 0 1440 320"
				preserveAspectRatio="none"
				xmlns="http://www.w3.org/2000/svg"
			>
				<defs>
					<linearGradient id="bg-gradient" x1="0%" y1="0%" x2="100%" y2="0%">
						<stop offset="0%" stop-color="#E6FFFA" />
						<stop offset="100%" stop-color="#EBF4FF" />
					</linearGradient>
				</defs>
				<path
					fill="url(#bg-gradient)"
					d="
                    M0,10 
                    C360,20 1420,40 10,20 
                    C1250,0 20,10 1440,0 
                    L1440,320 
                    L0,320 
                    Z"
				/>
			</svg>

			<div class="step-content-container">
				<div class="step-number">2.</div>
				<div class="step-content">
					<h3>Erstellen dein Lebenslauf</h3>
				</div>
			</div>
			<div class="step-illustration">
				<img src="/assets/asset2.svg" alt="Step 2 Illustration" />
			</div>
		</div>

		<div class="step">
			<div class="step-content-container">
				<div class="step-number">3.</div>
				<div class="step-content">
					<h3>Mit nur einem Klick bewerben</h3>
				</div>
			</div>
			<div class="step-illustration">
				<img src="/assets/asset3.svg" alt="Step 3 Illustration" />
			</div>
		</div>
	</section>
</main>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;500;600;700&display=swap');

	.job-website {
		font-family: 'Lato', sans-serif;
		min-height: 100vh;
		width: 100%;
	}

	.header {
		position: fixed;
        z-index: 2;
		width: 100%;
		height: 67px;
		display: flex;
		justify-content: flex-end;
		align-items: center;
		/* UI Properties */
		background: #ffffff 0% 0% no-repeat padding-box;
		box-shadow: 0px 3px 6px #00000029;
		border-radius: 0px 0px 12px 12px;
		opacity: 1;
		padding: 10px;
	}

	.login-btn {
		width: 39px;
		height: 19px;
		/* UI Properties */
		font: normal normal 600 14px/17px Lato;
		letter-spacing: 0.84px;
		color: #319795;
		opacity: 1;
	}

	.login-btn:hover {
		color: #2b6cb0;
	}

	.hero {
		width: 100%;
		height: 80vh;
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
		/* UI Properties */

		opacity: 1;
	}
	.hero::before {
		position: absolute;
		content: '';
		top: 0;
		left: 0;
		bottom: 0;
		right: 0;
		z-index: -1;
		transform: rotate(-2deg);
		background: linear-gradient(102deg, #ebf4ff 0%, #e6fffa 100%);
	}

	.content-container {
		width: 100%;
		height: 100%;
		text-align: center;
		display: flex;
		align-items: center;
		flex-direction: row;
		justify-content: space-around;
        margin-top: 10%;
	}

	.main-heading {
		width: 320px;
		height: 156px;
		/* UI Properties */
		text-align: left;
		font: normal normal bold 65px/78px Lato;
		letter-spacing: 1.95px;
		color: #2d3748;
		opacity: 1;
	}

	.register-btn {
		width: 320px;
		height: 40px;
		background: #319795;
		border: none;
		border-radius: 12px;
		text-align: center;
		font: normal normal 600 14px/17px Lato;
		letter-spacing: 0.84px;
		color: #e6fffa;
		opacity: 1;
		cursor: pointer;
		transition: all 0.3s ease;
	}

	.register-btn:hover {
		background: #2c7a7b;
		transform: translateY(-2px);
	}

	.handshake-icon {
		font-size: 120px;
		opacity: 0.8;
	}

	.user-selection {
		display: flex;
		justify-content: center;
	}

	.user-buttons {
		display: flex;
        width: 100%;
		justify-content: space-around;
		margin-top: 3%;
        padding: 2% 5%;
	}

	.user-btn {
        width:100%;
        padding:1% 5%;
		background: #ffffff;
		border: 1px solid #cbd5e0;
		font: normal normal 500 14px/17px Lato;
		color: #4a5568;
		cursor: pointer;
		transition: all 0.3s ease;
	}

	.user-buttons .user-btn:first-child {
		border-radius: 12px 0px 0px 12px;
	}

	.user-buttons .user-btn:last-child {
		border-radius: 0px 12px 12px 0px;
	}

	.user-btn:hover,
	.user-btn.active {
		background: #81e6d9 0% 0% no-repeat padding-box;
		color: #ffffff;
	}

	.steps-intro {
		text-align: center;
		margin-top: 5%;
	}

	.second-heading {
		text-align: center;
		font: 40px/48px Lato;
		letter-spacing: 0px;
		color: #4a5568;
		opacity: 1;
		margin: 0 auto;
	}

	.steps {
		width: 100%;
		margin: 0 auto;
		position: relative;
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-top: 3%;
	}

	.step-content-container {
		display: flex;
		justify-content: center;
		flex: 1;
		position: relative;
		align-items: baseline;
	}
	.svg-circle-bg {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		background: white;
		border-radius: 50%;
		aspect-ratio: 1 / 1;
		width: fit-content;
	}
	.hero::before {
		transform: none;
		background: linear-gradient(102deg, #ebf4ff 0%, #e6fffa 100%);
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		width: 100%;
		height: 100%;
		content: '';
		z-index: -1;
	}
	body {
		overflow-x: hidden;
	}
	.hero {
		width: 100%;
	}
    
	.svg-circle-bg img {
		display: block;
		height: 100%;
		width: 100%;
		border-radius: 50%;
	}
	.job-website {
		overflow-x: hidden;
	}
	.step {
		margin-top: 2%;
		margin-bottom: 5%;
		width: 100%;
		height: 30vh;
		display: flex;
		align-items: center;
		justify-content: space-around;
		position: relative;
	}

	.step-number {
		position: relative;
		text-align: center;
		font: normal 130px/156px Lato;
		letter-spacing: 0px;
		color: #718096;
		opacity: 1;
	}

	.step:nth-child(even) {
		flex-direction: row-reverse;
	}

	.step:first-of-type .step-number::before,
	.step:last-of-type .step-number::before {
		content: '';
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 230px;
		height: 230px;
		z-index: -1;
		border-radius: 50%;
		background: #f7fafc;
	}

	.step:last-of-type .step-number::before {
		top: 80%; /* Slightly lower */
	}

	.wave-shape {
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
		width: 100%;
		z-index: -1;
	}

	.step-content h3 {
		font: 30px/36px Lato;
		font-weight: 600;
		color: #718096;
	}

	.step-illustration {
		flex: 1;
		width: 100%;
		display: flex;
		justify-content: center;
	}

	#mobile-register-bar {
		display: none;
	}
	@media (max-width: 768px) {
		#web-register-button {
			display: none;
		}
		.content-container {
			flex-direction: column;
		}
        .step:nth-child(even) {
		flex-direction: column;
	}
		#mobile-register-bar {
			position: fixed;
			bottom: 0;
			left: 0;
			width: 100%;
			background: white;
			box-shadow: 0 -2px 6px rgba(0, 0, 0, 0.1);
			z-index: 1000;
			display: flex;
			justify-content: center;
			padding: 10px 1rem;
		}

		#mobile-register-bar .register-btn {
			width: 320px;
			height: 40px;
			background: #319795;
			border: none;
			border-radius: 12px;
			color: #e6fffa;
			font: normal normal 600 14px/17px Lato;
			letter-spacing: 0.84px;
			cursor: pointer;
			transition: all 0.3s ease;
		}
        .user-selection{
            width:100%
        }

		#mobile-register-bar .register-btn:hover {
			background: #2c7a7b;
			transform: translateY(-2px);
		}

		.hero {
			height: auto;
			padding: 40px 0;
			text-align: center;
		}

		.main-heading {
			font-size: 36px;
			line-height: 44px;
			width: auto;
			height: auto;
			text-align: center;
			margin-bottom: 20px;
		}

		.step {
			flex-direction: column;
			height: auto;
			padding: 20px 0;
		}

		.step-number {
			font-size: 60px;
			line-height: 1;
		}

		.step-content h3 {
			font-size: 20px;
			text-align: center;
		}

		.step-illustration {
			margin-top: 20px;
		}
        .user-buttons {
		display: flex;
		justify-content: space-between;
		margin-top: 3%;
        width: 100%;
        padding: 2% 5%;
	}

	.user-btn {
		flex:1;
        padding:1% 5%;
		background: #ffffff;
		border: 1px solid #cbd5e0;
		font: normal normal 500 14px/17px Lato;
		color: #4a5568;
		cursor: pointer;
		transition: all 0.3s ease;
	}
	}
</style>

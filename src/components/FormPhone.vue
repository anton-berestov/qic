<template>
	<form id="form" class="animated fadeIn">
		<div class="form-title">
			<div class="approximate">Get Insured in ~4 min</div>
			<div class="discount">10% discount for online registration</div>
		</div>
		<div class="form-group">
			<input
				class="input-form"
				type="tel"
				name="num"
				placeholder=" +974     Enter your phone"
				v-model="phone"
				:class="{
					notvalid: output === false,
					valid: output === true,
				}"
			/>

			<button class="btn-form" @click.prevent="Start">
				Get a Quote
			</button>
			<img class="flag" src="../assets/icon/flag.svg" />
		</div>
	</form>
</template>

<script>
	export default {
		name: 'Form',
		data() {
			return {
				failedValidation: {
					phone: '',
				},
				phone: '+974 ',
				output: true,
				noPhone: false,
			};
		},
		methods: {
			Start() {
				if (this.phone.length > 5) {
					const re = /^[+]*[(]{0,1}[0-9]{1,3}[)]{0,1}[-\s\./0-9]*$/g;
					console.log(this.phone);
					var valid = re.test(this.phone);
					if (valid) {
						this.output = true;
						this.phone = '';
						this.$router.push({ path: 'start' });
					}
				} else {
					this.output = false;
				}
			},
		},
	};
</script>

<style scoped>
	#form {
		position: absolute;
		width: 562px;
		height: 137px;
		left: 480px;
		top: 520px;
		padding: 0 24px 24px;
		background: #ffffff;
		border-radius: 30px;
		margin-bottom: 72px;
		display: grid;
	}
	.animated {
		-webkit-animation-duration: 6s;
		animation-duration: 6s;
		-webkit-animation-fill-mode: both;
		animation-fill-mode: both;
	}
	@-webkit-keyframes fadeIn {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	@keyframes fadeIn {
		0% {
			opacity: 0;
		}
		100% {
			opacity: 1;
		}
	}

	.fadeIn {
		-webkit-animation-name: fadeIn;
		animation-name: fadeIn;
	}
	.form-title {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.form-group {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.approximate {
		left: calc(50% - 219px / 2 - 154.5px);
		top: 24px;
		font-weight: 600;
		font-size: 22px;
		line-height: 110%;
		color: #141414;
	}

	.discount {
		top: calc(50% - 17px / 2 - 1px);
		font-weight: 600;
		font-size: 15px;
		line-height: 110%;
		display: flex;
		align-items: center;
		color: #0b66ba;
		background: rgba(11, 102, 186, 0.22);
		border-radius: 8px;
		padding: 3px 8px 5px;
		width: 267px;
		justify-content: center;
	}
	.input-form {
		width: 312px;
		height: 55px;
		left: 24px;
		top: 80px;
		background: #f0f4f7;
		border-radius: 16px;
		padding-left: 30px;
		font-weight: 500;
		font-size: 18px;
		line-height: 110%;
		color: #141414;
		outline: none;
		border: none;
		border: 4px solid #f0f4f7;
	}
	.input-form:focus {
		border: 4px solid rgba(11, 102, 186, 0.22);
	}
	.input-form:hover {
		border: 4px solid rgba(11, 102, 186, 0.22);
	}

	.notvalid {
		border: 4px solid rgb(245, 131, 131);
		color: rgb(245, 131, 131);
	}

	.flag {
		position: absolute;
		width: 24px;
		height: 24px;
		left: 30px;
		top: calc(51% + -2px);
	}

	.btn-form {
		width: 200px;
		height: 64px;
		left: 352px;
		top: 80px;
		font-weight: 600;
		font-size: 18px;
		line-height: 110%;
		color: #ffffff;
		background: #141414;
		border-radius: 16px;
		box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
	}
	.btn-form:hover {
		background: #586067;
		border: 4px solid #586067;
		box-shadow: none;
		box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.15);
	}
</style>

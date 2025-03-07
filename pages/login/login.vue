<template>
	<div class="login-container">
		<div class="login-header">
			<h1>选择你的角色</h1>
		</div>
		<div class="role-selection">
			<div class="role-card" @click="handleRoleSelect('user')">
				<div class="icon-wrapper">
					<uni-icons type="person-filled" size="32" color="#409EFF"></uni-icons>
				</div>
				<text>用户登录</text>
			</div>
			<div class="role-card" @click="handleRoleSelect('provider')">
				<div class="icon-wrapper">
					<uni-icons type="shop-filled" size="32" color="#409EFF"></uni-icons>
				</div>
				<text>商家登录</text>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	methods: {
		handleRoleSelect(role) {
			uni.setStorageSync('roleType', role)
			uni.redirectTo({
				url: '/pages/index?role=' + role,
			})
		}
	}
}
</script>

<style scoped>
.login-container {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	min-height: 100vh;
	background-color: #ffffff;
	padding: 20px;
}

.login-header {
	margin-bottom: 50px;
}

.login-header h1 {
	font-size: 24px;
	color: #333;
	font-weight: normal;
}

.role-selection {
	display: flex;
	gap: 40px;
}

.role-card {
	display: flex;
	flex-direction: column;
	align-items: center;
	gap: 12px;
	cursor: pointer;
	transition: transform 0.2s ease;
}

.role-card:active {
	transform: scale(0.95);
}

.icon-wrapper {
	width: 64px;
	height: 64px;
	border-radius: 16px;
	background-color: #f5f7fa;
	display: flex;
	align-items: center;
	justify-content: center;
}

.role-card text {
	font-size: 16px;
	color: #333;
}

@media (max-width: 480px) {
	.role-selection {
		gap: 30px;
	}
}
</style>

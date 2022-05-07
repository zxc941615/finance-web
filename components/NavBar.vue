<template>
	<v-app-bar>
		<v-app-bar-nav-icon></v-app-bar-nav-icon>
		<v-toolbar-title>Stock Information</v-toolbar-title>
		<v-container>
			<v-text-field outlined dense hide-details placeholder="輸入台股代號，查看公司價值"></v-text-field>    
		</v-container>
		

	</v-app-bar>
</template>
<script>

export default {
	setup() {
		
		return {
			
		}

	},
}
</script>
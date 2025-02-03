<script setup>
import { useLayout } from '@/layout/composables/layout';
import AppConfigurator from './AppConfigurator.vue';
import { ref } from 'vue';
const { toggleMenu, toggleDarkMode, isDarkTheme } = useLayout();

const display = ref(false);

function open() {
    display.value = true;
}

function close() {
    display.value = false;
}
</script>

<template>
    <div class="layout-topbar">
        <div class="layout-topbar-logo-container">
            <button class="layout-menu-button layout-topbar-action" @click="toggleMenu">
                <i class="pi pi-bars"></i>
            </button>
            <router-link to="/" class="layout-topbar-logo">
                <svg viewBox="0 0 300 300" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <image href="https://ssru.ac.th/datafiles/loadimg/SSRU_LOGO1.png" x="0" y="0" height="300" width="300" />
                </svg>
                <span>SSRU_RFID</span>
            </router-link>
        </div>

        <div class="layout-topbar-actions">
            <div class="layout-config-menu">
                <button type="button" class="layout-topbar-action" @click="toggleDarkMode">
                    <i :class="['pi', { 'pi-moon': isDarkTheme, 'pi-sun': !isDarkTheme }]"></i>
                </button>
                <div class="relative">
                    <button
                        v-styleclass="{ selector: '@next', enterFromClass: 'hidden', enterActiveClass: 'animate-scalein', leaveToClass: 'hidden', leaveActiveClass: 'animate-fadeout', hideOnOutsideClick: true }"
                        type="button"
                        class="layout-topbar-action layout-topbar-action-highlight"
                    >
                        <i class="pi pi-palette"></i>
                    </button>
                    <AppConfigurator />
                </div>
            </div>

            <button
                class="layout-topbar-menu-button layout-topbar-action"
                v-styleclass="{ selector: '@next', enterFromClass: 'hidden', enterActiveClass: 'animate-scalein', leaveToClass: 'hidden', leaveActiveClass: 'animate-fadeout', hideOnOutsideClick: true }"
            >
                <i class="pi pi-ellipsis-v"></i>
            </button>

            <div class="hidden layout-topbar-menu lg:block">
                <div class="layout-topbar-menu-content">
                    <Button icon="pi pi-user" rounded as="router-link" to="/auth/login" />
                    <Dialog header="SSRU_RFID" v-model:visible="display" :breakpoints="{ '960px': '75vw' }" :style="{ width: '40vw' }" :modal="true">
                        <div class="bg-surface-50 dark:bg-surface-950 flex items-center justify-center min-w-[20vw] overflow-hidden">
                            <!--min-h-screen -->
                            <div class="flex flex-col items-center justify-center">
                                <div style="border-radius: 56px; padding: 0.3rem; background: linear-gradient(180deg, var(--primary-color) 10%, rgba(33, 150, 243, 0) 30%)">
                                    <div class="w-full px-8 py-20 bg-surface-0 dark:bg-surface-900 sm:px-20" style="border-radius: 53px">
                                        <div class="mb-8 text-center">
                                            <router-link to="/" class="layout-topbar-logo">
                                                <svg viewBox="0 0 100 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                                                    <image href="https://ssru.ac.th/datafiles/loadimg/SSRU_LOGO1.png" x="40" y="0" height="20" width="20" />
                                                </svg>
                                                <span>SSRU_RFID</span>
                                            </router-link>
                                            <div class="mb-4 text-3xl font-medium text-surface-900 dark:text-surface-0">Welcome to PrimeLand!</div>
                                            <span class="font-medium text-muted-color">Sign in to continue</span>
                                        </div>

                                        <div>
                                            <label for="email1" class="block mb-2 text-xl font-medium text-surface-900 dark:text-surface-0">Email</label>
                                            <InputText id="email1" type="text" placeholder="Email address" class="w-full md:w-[30rem] mb-8" v-model="email" />

                                            <label for="password1" class="block mb-2 text-xl font-medium text-surface-900 dark:text-surface-0">Password</label>
                                            <Password id="password1" v-model="password" placeholder="Password" :toggleMask="true" class="mb-4" fluid :feedback="false"></Password>

                                            <div class="flex items-center justify-between gap-8 mt-2 mb-8">
                                                <div class="flex items-center">
                                                    <Checkbox v-model="checked" id="rememberme1" binary class="mr-2"></Checkbox>
                                                    <label for="rememberme1">Remember me</label>
                                                </div>
                                                <span class="ml-2 font-medium text-right no-underline cursor-pointer text-primary">Forgot password?</span>
                                            </div>
                                            <Button label="Sign In" class="w-full" as="router-link" to="/"></Button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <template #footer>
                            <Button label="Save" @click="close" />
                        </template>
                    </Dialog>
                    <Button label="Show" style="width: auto" @click="open" />
                </div>
            </div>
        </div>
    </div>
</template>

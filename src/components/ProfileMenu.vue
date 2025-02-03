<script>
export default {
    data() {
        return {
            showProfileDialog: false, // ควบคุม Dialog
            user: {
                name: 'John Doe',
                email: 'johndoe@example.com'
            }
        };
    },
    methods: {
        editProfile() {
            // เพิ่มฟังก์ชันแก้ไขข้อมูล
            console.log('Edit Profile Clicked');
        }
    }
};
</script>

<template>
    <div>
        <!-- ปุ่มสำหรับเปิด Profile Dialog -->
        <button @click="showProfileDialog = true" class="p-button p-button-rounded p-button-text">
            <i class="pi pi-user"></i>
        </button>

        <!-- Dialog Component -->
        <Dialog header="Profile" v-model:visible="showProfileDialog" :modal="true" :style="{ width: '30vw' }" :closable="true" class="p-dialog">
            <div class="text-center">
                <!-- รูปโปรไฟล์ -->
                <img src="/demo/images/avatar/profile.png" alt="Profile Picture" class="w-20 h-20 mx-auto rounded-full" />
                <h3 class="mt-3 text-xl font-semibold">{{ user.name }}</h3>
                <p class="text-sm text-gray-500">{{ user.email }}</p>
                <button @click="editProfile" class="w-full mt-4 p-button p-button-outlined">Edit Profile</button>
            </div>
        </Dialog>
    </div>
</template>

<style scoped>
/* ปรับแต่ง CSS ตามที่ต้องการ */
</style>

<template>
    <div class="upload-box" @dragover.prevent @drop="handleDragDrop">
        <input type="file" ref="fileInput" @change="handleFileUpload" accept="image/*" class="hidden" />
        <div class="drop-zone" @click="triggerFileInput">
            <div v-if="loading" class="loading-spinner">
                <div class="spinner"></div>
                <p>Uploading, please wait...</p>
            </div>
            <div v-else>
                <p>Drag & drop a file or <span class="browse">browse files</span></p>
                <p class="file-info">JPG, PNG or GIF - Max file size 2MB</p>
            </div>
        </div>
        <p v-if="error" class="error">{{ error }}</p>
    </div>
</template>

<script>
export default {
    name: 'FileUploader',
    props: {
        onFileUploaded: {
            type: Function,
            required: true
        }
    },
    data() {
        return {
            error: '',
            loading: false,
            uploadedLink: '' 
        };
    },
    methods: {
        triggerFileInput() {
            this.$refs.fileInput.click();
        },
        handleFileUpload(event) {
            const file = event.target.files[0];
            this.uploadFile(file);
        },
        handleDragDrop(event) {
            const file = event.dataTransfer.files[0];
            this.uploadFile(file);
        },
        uploadFile(file) {
            if (!file) {
                this.error = 'Please select a file.';
                return;
            }

            if (file.size > 2 * 1024 * 1024) { 
                this.error = 'File size exceeds the 2MB limit.';
                return;
            }

            this.error = '';
            this.loading = true;
            const fileURL = URL.createObjectURL(file); 

            const reader = new FileReader();
            reader.onload = (e) => {
                setTimeout(() => {
                    this.loading = false;
                    const fileData = e.target.result;

                    this.uploadedLink = fileURL; 

                    this.$emit('file-uploaded', this.uploadedLink);
                }, 2000); 
            };
            reader.readAsDataURL(file);
        },
        copyToClipboard() {
            if (!this.uploadedLink) return;
            navigator.clipboard.writeText(this.uploadedLink).then(() => {
            }).catch(() => {
                alert('Failed to copy the link.');
            });
        }
    }
};
</script>

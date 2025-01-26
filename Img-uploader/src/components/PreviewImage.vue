<template>
    <div v-if="imageUrl" class="preview">
        <img :src="imageUrl" alt="Uploaded Preview" />
        <button class="share-btn" @click="shareImage">Share</button>
        <button class="download-btn" @click="downloadImage">Download</button>
    </div>
</template>

<script>
export default {
    name: 'PreviewImage',
    props: {
        imageUrl: {
            type: String,
            required: true
        }
    },
    data() {
        return {
            shareLink: ''
        };
    },
    watch: {
        imageUrl(newImageUrl) {
            this.generateShareLink(newImageUrl);
        }
    },
    methods: {
        generateShareLink(imageUrl) {
            this.shareLink = imageUrl; 
        },
        shareImage() {
            alert('Image link copied to clipboard: ' + this.shareLink);
            this.copyToClipboard();
        },
        copyToClipboard() {
            navigator.clipboard.writeText(this.shareLink).then(() => {
            }).catch(() => {
                alert('Failed to copy link.');
            });
        },
        downloadImage() {
            const link = document.createElement('a');
            link.href = this.imageUrl;
            link.download = 'downloaded-image';
            link.click();
        }
    },
    mounted() {
        this.generateShareLink(this.imageUrl);
    }
};

</script>

<style scoped>
.preview {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
}

.share-btn,
.download-btn {
    padding: 5px 10px;
    border: none;
    background-color: #007BFF;
    color: white;
    cursor: pointer;
    border-radius: 4px;
}

.share-btn:hover,
.download-btn:hover {
    background-color: #0056b3;
}

.share-link .link {
    color: #007BFF;
    cursor: pointer;
    text-decoration: underline;
}
</style>
<template>
    <div>
        <div class="content-section introduction">
            <div class="feature-intro">
                <h1>Message</h1>
                <p>Messages is used to display inline messages with various severities.</p>
            </div>
        </div>

        <div class="content-section implementation">
            <h3 class="first">Severities</h3>
            <Message severity="success">Order Submitted</Message>
            <Message severity="info">PrimeVue Rocks</Message>
            <Message severity="warn">There are unsaved changes</Message>
            <Message severity="error">Validation Failed</Message>

            <h3>Dynamic</h3>
            <Button label="Show" @click="addMessages()" />
            <Button label="Clear" @click="removeMessages()" class="p-button-secondary"/>
            <Message v-for="msg of messages" :severity="msg.severity" :key="msg.content">{{msg.content}}</Message>

            <h3>Auto Dismiss</h3>
            <Message severity="warn" :life="5000" :sticky="false">This message will hide in 5 seconds.</Message>

            <h3>Validation Message</h3>
            <div class="p-grid">
                <div class="p-col-12">
                    <InputText placeholder="Username" class="p-error" />
                    <ValidationMessage>Field is required</ValidationMessage>
                </div>
                <div class="p-col-12">
                    <InputText placeholder="Email" class="p-error" :closable="false" />
                    <ValidationMessage />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            messages: [],
            count: 0
        }
    },
    methods: {
        addMessages() {
            this.messages = [
                {severity: 'info', content: 'Dynamic Info Message'},
                {severity: 'success', content: 'Dynamic Success Message'},
                {severity: 'warn', content: 'Dynamic Warning Message'}
            ]
        },
        removeMessages() {
            this.messages = null;
        }
    }
}
</script>

<style lang="scss">
button.p-button {
    margin-right: .5em;
}

.p-inputtext {
    margin-right: .25em;
}
</style>

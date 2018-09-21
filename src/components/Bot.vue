<template>
    <div>
        <p>Botname: {{postObject.botName}}</p>
        <p>AttackValue: {{postObject.attackValue}}</p>
        <p>healthValue: {{postObject.healthValue}}</p>
        <hr>
    </div>
</template>
        
        <script>
        export default {
            props: ['postObject']
        }
        </script>
        

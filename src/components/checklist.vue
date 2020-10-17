<template>
<div>
<div>{{ruleSet}}}</div>
</div>
</template>

<script>
import ruleSet from "./ruleset.json"
export default {
    data: function(){
        return{
           ruleSet:ruleSet,

        }
    }
}
</script>

<style>

</style>
/*
Copyright 2020 SkillTree

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
*/
<template>
    <div class="res">
        <pre>
            <code>{{ result }}</code>
        </pre>
    </div>
</template>

<script>
    import {SkillsReporter} from '@skilltree/skills-client-vue';

    export default {
        name: "HelloWorldGlobalEventHandler",
        data() {
            return {
                result: '',
            };
        },
        created() {
            // just so we can always see the response
            SkillsReporter.configure({
                notifyIfSkillNotApplied: true,
            });
            SkillsReporter.addSuccessHandler(this.update);
        },
        methods: {
            update(result) {
                this.result = result;
            }
        },
    }
</script>

<style scoped>
    pre {
        margin: auto;;
        padding: 1rem;
        border: 1px solid #dddddd !important;
        overflow: auto;
        border-radius: 6px;
        background-color: #f6f8fa;
        min-height: 3rem;
        max-width: 80rem;

    }

    .res {
        text-align: center;
    }
</style>

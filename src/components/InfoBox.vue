<template lang="html">
  <div class="tip" :class="classType" v-if="isActive">
    <p>
      <slot name="box-body"></slot>
    </p>
  </div>
</template>

<script>
export default {
    name: "Box",
    data() {
        return {
            isActive: false,
            boxType: 'info'
        }
    },
    props: {
        active: {
            type: Boolean,
            required: true,
            default: false
        },
        type: {
            type: String,
            required: true,
            default: 'info'
        }
    },
    created() {
        this.isActive = this.active
        this.boxType = this.type
    },
    methods: {

    },
    computed: {
        classType: function() {
            switch (this.boxType) {
                case 'info':
                    return {
                        'info': true
                    }

                case 'warning':
                    return {
                        'warning': true
                    }

                case 'error':
                    return {
                        'error': true
                    }

                default:
                    return {
                        'info': true
                    }
            }
        }
    }
}
</script>

<style lang="css">

div.tip {
    padding: 8px 16px;
    border-radius: 4px;
    margin: 20px 0;

}

div.tip.info {
    border-left: 5px solid #50bfff;
    background-color: #ecf8ff;
}


div.tip.warning {
    background-color: rgba(255, 237, 202, 0.47843137254901963);
    border-left: 5px solid rgb(255, 114, 91);
}

div.tip.error {
    background-color: #fff6f7;
    border-left: 5px solid #fe6c6f;
}

div.tip p {
    font-size: 13px !important;
}

div.tip li {
    margin-left: 0 !important;
    border: 0 !important;
    line-height: 1.2em !important;
    color: #48494a !important;
}

div.tip li:before {
    content: "\21AA" !important;
    float: left !important;
    position: relative;
    margin-right: 3px;
}

div.tip ul {
    list-style-type: none !important;
    -webkit-padding-start: 0 !important;
    padding-left: 0 !important;
}
</style>

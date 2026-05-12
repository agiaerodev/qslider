<template></template>
<script>
export default {
  data() {
    return {
      crudId: this.$uid(),
    };
  },
  computed: {
    crudData() {
      return {
        crudId: this.crudId,
        entityName: config('main.qslider.entityNames.slide'),
        apiRoute: 'apiRoutes.qslider.slides',
        permission: 'slider.slides',
        //extraFormFields: 'Slider.crud-fields.slides',
        create: {
          title: this.$tr('slider.cms.newSlide'),
        },
        read: {
          columns: [],
          //requestParams: { include: 'files' },
        },
        update: {
          title: this.$tr('slider.cms.updateSlide'),
          requestParams: { include: 'files' },
        },
        delete: true,
        formLeft: {
          id: { value: '' },
          userId: { value: this.$store.state.quserAuth.userId },
          title: {
            value: '',
            type: 'input',
            isTranslatable: false,
            props: {
              label: `${this.$tr('isite.cms.form.title')}`,
            },
          },          
          
          url: {
            value: '',
            type: 'input',
            isTranslatable: false,
            props: {
              label: 'URL',
            },
          },
          
          summary: {
            value: '',
            type: 'input',
            isTranslatable: false,
            props: {
              type: 'textarea',
              label: `${this.$tr('isite.cms.form.summary')}`,
            },
          },
          description: {
            value: '',
            type: 'html',
            isTranslatable: false,
            props: {
              label: `${this.$tr('isite.cms.form.description')}`,
            },
          },
        },
        formRight: {
          status: {
            value: true,
            type: 'select',
            isTranslatable: false,
            props: {
              label: this.$tr('isite.cms.form.status'),
              options: [
                { label: this.$tr('isite.cms.label.enabled'), value: true },
                { label: this.$tr('isite.cms.label.disabled'), value: false },
              ],
            },
          },
          target: {
            value: null,
            type: 'select',
            props: {
              label: 'Target:',
              options: [                
                { label: 'New tab', value: '_blank' },
                { label: 'Same tab', value: '_self' },
              ],
            },
          },
          buttonsType: {
            value: null,
            type: 'select',
            props: {
              label: 'Buttons Type:',
              options: [                
                { label: 'Type-1', value: 'type_1' },
                { label: 'Type-2', value: 'type_2' },
              ],
            },
          },       

          buttons: {          
            type: 'json',
            props: {label: 'Buttons'}
          }, 
          
          mainimage: {
            value: null,
            type: 'attachFiles',
            props: {
              zone: 'mainimage',
              entityType: 'Idata.Entities.Slider.Slide',
              type: 'attachFiles',
              class: 'tw-py-4 tw-justify-center',
            },
          },
        },
      };
    },
    //Crud info
    crudInfo() {
      return this.$store.state.qcrudComponent.component[this.crudId] || {};
    },
  },
};
</script>

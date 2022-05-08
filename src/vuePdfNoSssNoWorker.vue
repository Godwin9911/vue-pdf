<style src="./annotationLayer.css"></style>
<script>

	import componentFactory from './componentFactory.js'

	if ( import.meta.env.VUE_ENV !== 'server' ) {

		var pdfjsWrapper = import('./pdfjsWrapper.js').default;
		var PDFJS = import('pdfjs-dist/es5/build/pdf.js');
		var component = componentFactory(pdfjsWrapper(PDFJS));
	} else {

		var component = componentFactory({});
	}

	export default component;
</script>

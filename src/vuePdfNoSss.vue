<style src="./annotationLayer.css"></style>
<script>

	import componentFactory from './componentFactory.js'

	if ( import.meta.env.VUE_ENV !== 'server' ) {

		var pdfjsWrapper = import('./pdfjsWrapper.js').default;
		var PDFJS = import('pdfjs-dist/es5/build/pdf.js');

		if ( typeof window !== 'undefined' && 'Worker' in window && navigator.appVersion.indexOf('MSIE 10') === -1 ) {

			var PdfjsWorker = import('worker-loader!pdfjs-dist/es5/build/pdf.worker.js');
			PDFJS.GlobalWorkerOptions.workerPort = new PdfjsWorker();
		}

		var component = componentFactory(pdfjsWrapper(PDFJS));
	} else {

		var component = componentFactory({});
	}

	export default component;
</script>

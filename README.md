###### Tunelea tu Ingress ######

k8s


Instala Cloudflred


cloudflared tunnel login


cat ~/.cloudflared/cert.pem



Instala tu app, no necesitas configurar el Ingress


	curl --proto '=https' --tlsv1.2 -sSfL https://run.linkerd.io/emojivoto.yml \
	  | kubectl apply -f -
  
Mira si ya corre:  
  
	k get pods -n emojivoto



Muestralo:

	kubectl -n emojivoto port-forward svc/web-svc 8080:80


Funciona?


Ahora crea el tunel

	cloudflared tunnel create emojivoto-tunnel


	kubectl create secret generic tunnel-credentials \
	--from-file=credentials.json=$HOME/.cloudflared/66a54e1f-afc4-44e7-a11c-9c25a9cea11b.json  
	

Descarga el manifiesto:



     wget https://github.com/cloudflare/argo-tunnel-examples/blob/master/named-tunnel-k8s/cloudflared.yaml
     
     
     mv cloudflared.yaml cloudflared-emojivoto.yaml
     
     
     vim cloudflared-emojivoto.yaml
     
     
Crear el CNAME
 
     emojivoto
     66a54e1f-afc4-44e7-a11c-9c25a9cea11b.cfargotunnel.com
     











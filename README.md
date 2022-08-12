# simple-oke-demo
Walkthrough for simple OKE demo

Section 1: Pull Image from Kominfo and Push to OCIR
1. Prepare repository
	1. Go to Developer Services - Container Registry (Under Containers & Artifacts group)
	2. Create repository by hitting "Create repository" button and put the name for repository (repo name will be used for docker tag and docker push later)
  3. Take note on the repository namespace (E.g.: axmmgq8syyah)
2. Get authentication token
	1. Go to user menu in the top-right of OCI console
  2. Click on "User Settings" -- "Auth Tokens" (Under Resources on the bottom-left)
  3. Click on "Generate Token" button and put informative description *Don't forget to copy the generated token since it won't be shown again
3. Pull image and push to OCIR
  1. Open up Cloud Shell terminal
  2. Login to Kominfo repo by typing up: docker login registry-splp.layanan.go.id/sso/sso-layanan:659 -u oracledev_token
  3. Paste the auth token provided by kominfo when prompted for password: 2xQpYy4x2kz58RCmWaaZ
  4. Pull the image by typing up: docker pull registry-splp.layanan.go.id/sso/sso-layanan:659
  5. Validate that docker image already downloaded by executing: docker images
  6. Tage the image by executing: docker tag registry-splp.layanan.go.id/sso/sso-layanan:659 ap-singapore-1.ocir.io/axmmgq8syyah/demo-registry:latest
    Notes: ap-singapore-1.ocir.io/axmmgq8syyah/demo-registry:latest --> {OCIR region repo}/{repo namespace}/{repo name}:{version tag}
  7. Login to OCIR repo by typing up: docker login ap-singapore-1.ocir.io
  8. Type username by following this format: {repository namespace}/{OCI username} --> e.g.: axmmgq8syyah/lucky.sutanto@oracle.com
  9. Paste the auth token that previously generated on previous step
  10. Push the docker image which previously has been tagged by executing: docker push ap-singapore-1.ocir.io/axmmgq8syyah/demo-registry:latest 

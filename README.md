# Using OpenShift GitOps to Deploy VMs in OpenShift Virtualization
This lab is based off a [Developer hub lab](https://developers.redhat.com/learning/learn:manage-openshift-virtual-machines-gitops/resource/resources:connect-and-configure-external-repository-argo-cd-virtual-machines)
## Lab Instructions
1. Make a fork of this repo and make sure your fork is **public**
2. In `overlays/kustomization.yaml` change the `namespace` value to `gitops-{your user}`
```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
namespace: gitops-user6
...
```
3. Log into the OpenShift web console, go to **Virtualization > Virtual Machines** from the left hand menu and select the `gitops-{your user}` project at the top of the screen
  ![Step 3](images/step3.png)

4. Open The AroCD Console and log in
- Click the grid in the top right menu bar and select Cluster ArgoCD
  ![Step 4.1](images/step4-1.png)
- Select login via OpenShift and enter your OpenShift username and password

  ![Step 4.2](images/step4-2.png)
- Enter your OpenShift username and password
  ![Step 4.3](images/step4-3.png)
On the next screen you will see all of the GitOps applications on the cluster. Feel free to explore but don't change any of the other applications

5. Add your GitHub Respository as a repository
- Go to Settings > Repositories

  ![Step 5.1](images/step5-1.png)
- Press Connect Repo

  ![Step 5.2](images/step5-2.png)
- Select VIA HTTPS
- Enter your repos URL under Repository URL
- Click Connect

  ![Step 5.3](images/step5-3.png)

6. Return to the Applications pane and create a New App With the following info:

  ![Step 6.1](images/step6-1.png)
- Application Name: **{your user}-gitops-vms**
- Project Name: **default**
  ![Step 6.2](images/step6-2.png)
- Repository URL: *Select the repository you added in the previous step*
- Path: *Select **overlays***
  ![Step 6.3](images/step6-3.png)
- Cluster URL: *Select **https://kubernetes.default.svc***
- Namespace: **gitops-user6**
  ![Step 6.4](images/step6-4.png)

7. Wait for resources to get provisioned and the application to be in a Synced state (this will take some time)

## Challenges
### Expose the application via services
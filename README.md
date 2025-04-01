# Using OpenShift GitOps to Deploy VMs in OpenShift Virtualization
## Lab Instructions
1. Make a fork of this repo and make sure your fork is **public**
2. In `overlays/kustomization.yaml` change the `namespace` value to `gitops-{your user}`
```
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
namespace: gitops-user6
...
```
3. In your OpenShift console, create the `gitops-{your user}` project and give it the `argocd.argoproj.io/managed-by=openshift-gitops` label
<!-- TODO: Images -->

4. Open The AroCD Console
- Click the grid in the top menu bar
<!-- TODO: Images -->
- Login via OpenShift
<!-- TODO: Images -->
- Enter your OpenShift username and password
<!-- TODO: Images -->

5. Add your GitHub Respository as a repository
- Go to Settings > Repositories
- Press Connect Repo
- Select VIA HTTPS
- Enter your repos URL under Repository URL
- Connect

6. Create a New App With the following info:
- Application Name: **{your user}-gitops-vms**
- Project Name: **default**
- Repository URL: *Select the repository you added in the previous step*
- Path: *Select **overlays***
- Cluster URL: *Select **https://kubernetes.default.svc***
- Namespace: **gitops-user6**

7. Wait for resources to get provisioned

## Challenges
### Expose the application via services
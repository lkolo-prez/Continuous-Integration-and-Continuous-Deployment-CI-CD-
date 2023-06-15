
```markdown
# Argo CD Installation

To install Argo CD, follow the steps below:

1. Create the `argocd` namespace:

   ```shell
   kubectl create namespace argocd
   ```

2. Apply the Argo CD installation manifest:

   ```shell
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```

3. Patch the Argo CD service to use a LoadBalancer:

   ```shell
   kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
   ```

4. Retrieve the initial admin password:

   ```shell
   kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
   ```

5. Decode the password:

   ```shell
   echo <password> | base64 --decode
   ```

Replace `<password>` with the actual value from the previous step.

These steps will create the `argocd` namespace, deploy Argo CD using the provided installation manifest, configure a LoadBalancer for the Argo CD server, and retrieve the initial admin password.

For more information and advanced configurations, refer to the [Argo CD documentation](https://argoproj.github.io/argo-cd/).

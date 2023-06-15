
# Argo CD Installation

To install Argo CD and perform necessary configurations, follow the steps below:

1. Create the `argocd` namespace:

   ```shell
   kubectl create namespace argocd
   ```

2. Apply the Argo CD installation manifest:

   ```shell
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```

3. Check the status of the Argo CD installation:

   ```shell
   kubectl get all -n argocd
   ```

4. Patch the Argo CD service to use a LoadBalancer:

   ```shell
   kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
   ```

5. Get the IP address of the Argo CD service:

   ```shell
   kubectl get services --namespace argocd argocd-server --output jsonpath='{.status.loadBalancer.ingress[0].ip}'
   ```

6. Forward the Argo CD server port to localhost:

   ```shell
   kubectl port-forward svc/argocd-server -n argocd 8080:443
   ```

7. Retrieve the initial admin password:

   ```shell
   kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
   ```

8. From your Ubuntu terminal, log in to Argo CD using the Argo CD server IP:

   ```shell
   argocd login <ip-hosta>
   ```

9. Add the Git repository to Argo CD:

   ```shell
   argocd repo add git@github.com:<github-repo-name>.git --ssh-private-key-path <ssh-path> --name ecommerce-cicd --type git
   ```

Replace the placeholders `<ip-hosta>`, `<github-repo-name>`, `<ssh-path>` with the actual values specific to your setup.

These steps will create the `argocd` namespace, deploy Argo CD using the provided installation manifest, configure a LoadBalancer for the Argo CD server, retrieve the initial admin password, and add the Git repository to Argo CD for CI/CD purposes.

For more information and advanced configurations, refer to the [Argo CD documentation](https://argoproj.github.io/argo-cd/).

# traefik-helm-argocd

This project provides a Helm chart for deploying Traefik, a popular ingress controller for Kubernetes, using Argo CD for continuous delivery.

## Project Structure

- **charts/traefik/**: Contains the Helm chart for Traefik.
  - **Chart.yaml**: Metadata about the Traefik Helm chart.
  - **values.yaml**: Default configuration values for the Traefik Helm chart.
  - **templates/deployment.yaml**: Kubernetes deployment manifest for Traefik.

- **argocd/**: Contains the Argo CD application manifest.
  - **traefik-app.yaml**: Defines the Argo CD application for deploying the Traefik Helm chart.

## Installation Instructions

1. **Prerequisites**:
   - Ensure you have a Kubernetes cluster up and running.
   - Install Helm and Argo CD on your local machine.

2. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd traefik-helm-argocd
   ```

3. **Install the Traefik Helm Chart**:
   Use the following command to install the Traefik Helm chart:
   ```bash
   helm install traefik ./charts/traefik
   ```

4. **Deploy with Argo CD**:
   - Apply the Argo CD application manifest:
   ```bash
   kubectl apply -f argocd/traefik-app.yaml
   ```

5. **Access Traefik Dashboard**:
   - After deployment, you can access the Traefik dashboard by port-forwarding:
   ```bash
   kubectl port-forward service/traefik 8080:80
   ```

   Then navigate to `http://localhost:8080/dashboard/` in your web browser.

## Customization

You can customize the Traefik deployment by modifying the `values.yaml` file in the `charts/traefik/` directory. This allows you to change settings such as service type, ingress configurations, and resource limits.

## License

This project is licensed under the MIT License. See the LICENSE file for details.
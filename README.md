# hemi-docker

## Running the hemi-min RPC Profile

This profile runs the minimum components required to interact with dApps on the Hemi network, relying on external Ethereum RPC endpoints.

**Requirements:**

*   **CPU Cores:** 2
*   **RAM:** 12GB
*   **Storage:** 2TB
*   **Software:** Docker and Docker Compose
*   **External Endpoints:**
    *   Ethereum Execution Layer RPC URL
    *   Ethereum Beacon Layer RPC URL

**Steps:**

1.  **Prerequisites:** Ensure Docker is installed and running, and your system meets the resource requirements.
2.  **Configure Environment:** Set environment variables for your Ethereum RPC endpoints (e.g., `ETHEREUMENDPOINTEXECUTION=<your_execution_rpc_url>`, `ETHEREUMENDPOINTBEACON=<your_beacon_rpc_url>`). Confirm the exact variable names required by the project.
3.  **Navigate to Project Directory:** Open a terminal and navigate to the `hemi-docker/localnode` directory.
4.  **Run Docker Compose:** Execute the command: `docker compose --profile hemi-min up -d`
5.  **Verify:**
    *   Check container logs (`docker compose logs -f`) for messages indicating successful connections to the external Ethereum Execution and Beacon Layer RPCs.
    *   Confirm the Hemi RPC endpoint is responsive. By default, this might be `http://localhost:8545`. You can test it with `curl`:
      ```bash
      curl -X POST -H "Content-Type: application/json" --data '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}' http://localhost:8545
      ```
      You should receive a JSON response with the current block number.

**Synchronization Time:**

Since this profile uses external Ethereum RPCs, there's no lengthy synchronization process for the Ethereum layers. The Hemi services should be operational in 2 days time
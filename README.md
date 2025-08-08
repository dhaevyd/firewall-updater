# 🔥 Firewall Updater

**Firewall Updater** is a lightweight Python utility, packaged as a Docker image, designed to **automatically update your cloud firewall ingress rules with your machine’s current public IP address** — so you never get locked out of your infrastructure again.

---

## 🚀 Why This Matters (The BEST Reason)

Dynamic IP addresses are the bane of secure remote access. If your IP changes unexpectedly, your firewall rules block your access — causing downtime, frustration, and wasted time. This tool transforms your firewall into a *dynamic, self-healing gatekeeper* that adapts instantly whenever your IP changes.

For sysadmins and DevOps engineers, this means:
- **Zero downtime** caused by IP mismatches
- Seamless remote management without emergency VPN setups
- Confidence that your critical servers remain accessible and secure

In short: it’s your *reliability insurance* for remote access.

---

## 🛠 How It Works (Inside Docker)

1. The Docker container boots a minimal Python environment with all dependencies.
2. On each run, the script:
   - Reads OCI API credentials from a mounted config volume.
   - Retrieves the current public IP from a trusted external service.
   - Updates the OCI Security List ingress rule accordingly.
3. The container exits immediately, designed for scheduled or on-demand runs.

---

## 📦 Requirements

- Oracle Cloud Infrastructure API key pair + `.oci/config` file  
  [Setup OCI CLI Config](https://docs.oracle.com/en-us/iaas/Content/API/Concepts/sdkconfig.htm)
- Docker installed on your host machine
- OCI **VCN ID** and **Security List ID** for your firewall rules

---

## 📂 Example `.oci/config`

```ini
[DEFAULT]
user=ocid1.user.oc1..aaaa...
fingerprint=20:3b:97:...
key_file=/root/.oci/oci_api_key.pem
tenancy=ocid1.tenancy.oc1..aaaa...
region=us-ashburn-1

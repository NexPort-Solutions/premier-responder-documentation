# Troubleshooting Activation of Premier Responder

## Premier Responder Activate Online Button is Grayed Out (disabled)

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Example of Disabled Activate Online Button</p></figcaption></figure>

Premier Responder uses an activation system called SoftWareKey. In order to activate systems online the local workstation with Premier Responder must have internet access and be able to "ping" the `secure.softwarekey.com` domain.&#x20;

If the "Activate Online" button is disabled, try the following steps to determine if the workstation can reach the SoftwareKey servers:

1. Open a windows command prompt.
2. From the command prompt, type in the following command and hit return.

{% code fullWidth="true" %}
```powershell
ping secure.softwarekey.com
```
{% endcode %}



The prompt should return something similar to this:

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

If the prompt returns an error please contact your system administrator. The following firewall rules may be required:

### Firewall Rules <a href="#win" id="win"></a>

You will need to allow outbound and inbound ping from the SoftwareKey Servers.&#x20;

* Echo request (ping) ICMP type 8
* Echo reply (pong) ICMP type 0

[Read the instructions from SoftwareKey here.](https://support.softwarekey.com/article/638-client-activation-ports-and-solo-server-ip-address)

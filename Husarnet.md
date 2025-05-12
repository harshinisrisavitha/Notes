installed directly on your devices.

<span style="color: rgb(185, 106, 217);">password:harshini@mars123</span>

**global scale peer-to-peer network** that allows you to connect your devices **directly in a secure and easy way**, even if they are behind NAT or firewall.Each device has its own IP address.WE can share devices

`husarnet`, which is CLI program you will use on day-to-day basis

`husarnet-daemon`, which is typically managed by `systemd` (or platforms' equivalent) and is not intended to be used directly

All three versions should match.

https://docs.husarnet.com/

<span style="color: rgb(224, 62, 45);">:        husarnet status</span>

<span style="color: rgb(224, 62, 45);">:        husarnet join JOIN_CODE HOST_NAME</span>

The concept is simple: if given IPv6 address is on the whitelist, then it can send packets to current device.

Additionally, there will be flags indicating status of the connection:

- Activity: you will see `⚪ inactive` if the peer is acknowledged, but the connection to given peer is not established yet. You will see `🟢 active` if there is a connection.
    
- Data flow: you will see `⚪ no data flow` if the peer is known, but the data is not exchanged at the moment (peer is idle). You will see `🟢 secure` if data is transmitted through Husarnet link.
    
- P2P status: you will see `🟢 peer to peer` if there is direct link between current device and given peer (Base Server does not take part in data exchange) and `🟡 tunelled` if the data has to be forwared through Base Server (because P2P link was not obtainable).
    

<span style="color: rgb(45, 194, 107);">harshini@harshini-Inspiron-14-5410-2-in-1:~$ husarnet join fc94:b01d:1803:8dd8:b293:5c7d:7639:932a/CkVDWKzBUdVemKST6s6KoS harshini</span>  
 <span style="color: rgb(45, 194, 107);">ERROR: Error reading secret file, are you root/administrator? open /var/lib/husarnet/daemon_api_token: permission denied</span>

<span style="color: rgb(45, 194, 107);">This operation requires superuser access. Rerun with sudo? \[y/N\]: Yes</span>

&nbsp;<span style="color: rgb(45, 194, 107);">SUCCESS: Successfully registered a join request</span>  
 <span style="color: rgb(45, 194, 107);">SUCCESS: Waiting for Base server connection (any protocol)…</span>  
 <span style="color: rgb(45, 194, 107);">SUCCESS: Waiting for websetup connection…</span>  
 <span style="color: rgb(45, 194, 107);">SUCCESS: Waiting until the device is joined…</span>

<span style="color: rgb(0, 0, 0);">waiting for the Husarnet Base server to confirm the join and complete the peer setup</span>

<span style="color: rgb(0, 0, 0);">![103d3aefa7f5ca5139293020d5dfa845.png](../_resources/103d3aefa7f5ca5139293020d5dfa845.png)</span>

#### . **Open Husarnet Web UI**

Go to https://app.husarnet.com and:

- **Log in** using the same email/account tied to your Husarnet network.
    
- Look for your device name (you passed `harshini` as the device name).
    
- It should appear under **"Pending Devices"** or something like "Waiting for Approval."
    

👉 Click **Approve** or **Assign** it to a network if prompted.

#### 3\. **Assign Device to Network (if needed)**

If the device isn’t automatically in your desired network:

- Go to your desired network.
    
- Click “+ Add device”
    
- Use the **Join Code** you already did:
    

That code is basically like a party invite 🥳.

The **data** exchanged between your devices is sent directly between them, with no central server in between if they can connect to each other directly. If they can't, there's a fallback method of exchanging the data over Husarnet servers, but don't worry - it's still encrypted so we won't be able to see the content of those messages. You'll also be able to check whether the connection is direct or tunnelled.

The traffic is sent using **UDP** instead of TCP which helps with reducing the latency over the network.
# 2.2-Tenants-vs-Subscriptions-The-Trust-Relationship
Madhat Cloud Security/Azure Labs


"A tenant holds identities. A subscription holds resources." Is the main note of this article and Ill be going through a walkthrough to identify different parts of identifying subscription details.

Q1
<img width="1181" height="319" alt="image" src="https://github.com/user-attachments/assets/1d907ed3-a195-4dcc-8a51-208e82a17407" />

Answer
<img width="1912" height="914" alt="image" src="https://github.com/user-attachments/assets/ae34063f-06da-4c98-9eb7-15bff6cf2f09" />


Q2
<img width="1155" height="310" alt="image" src="https://github.com/user-attachments/assets/51b2ba57-a7db-4ca7-b81a-fba69d92a20f" />

Answer
<img width="1912" height="914" alt="image" src="https://github.com/user-attachments/assets/bbdc8e62-ec77-40d6-8b01-e6784e5d2b0a" />

"Understanding the scope matters when you're locking things down. An identity that only holds a role on one resource group can only hurt that one resource group, no matter how many subscriptions exist. That's the entire reason your operative account is Reader on resource groups only (for now). If your credentials are stolen, the blast radius is a handful of read-only resource groups. Not the tenant, not the subscription, and not the other operatives. Mad Hat Labs is designed that way on purpose. You're living inside a least-privilege model, and now you can see the logic behind the walls."

Why that's defensive

This is what "blast radius" means. If an attacker phishes your credentials, they get exactly what you had: read-only access to a few resource groups. They can't delete anything, can't create VMs, can't grant themselves more rights (Reader can't modify role assignments), can't see other operatives' resource groups, and can't touch subscription or tenant settings.

Compare that to someone who's Owner at the subscription level. If their account is stolen, the attacker can read, change, or delete everything in that subscription and hand out access to anyone they want. Same stolen password, much bigger disaster.

An example of this is me trying to go to a resource group within the subscription and checking my access from the "Access Control"

<img width="1912" height="914" alt="image" src="https://github.com/user-attachments/assets/a94c75bc-1d37-4f76-8a27-167455bb9b5f" />

No access :(

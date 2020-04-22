### Use aws-cli to list instances with their IPS and their name


- To use aws-cli to list instances with their
  - Instance ID
  - Instance State
  - Instance Type
  - Instance PrivateIpAddress,
  - Instance PrivateDnsName
  - Instance PublicIpAddress
  - Instance PublicDnsName
  - Instance Name

```bash
aws ec2 describe-instances --query 'Reservations[*].Instances[*].[Tags[?Key==`Name`].Value[],InstanceId,State.Name,InstanceType,PrivateIpAddress,PrivateDnsName,PublicIpAddress,PublicDnsName]' --output json | tr -d '\n[] "' | perl -pe 's/i-/\ni-/g' | tr ',' '\t' | sed -e 's/null/None/g' | grep '^i-' | column -t
```
### Example
```bash
| ==> aws ec2 describe-instances --query 'Reservations[*].Instances[*].[Tags[?Key==`Name`].Value[],InstanceId,State.Name,InstanceType,PrivateIpAddress,PrivateDnsName,PublicIpAddress,PublicDnsName]' --output json | tr -d '\n[] "' | perl -pe 's/i-/\ni-/g' | tr ',' '\t' | sed -e 's/null/None/g' | grep '^i-' | column -t
i-077**************  stopped  t2.large    **.*1.**.**   ip-**-**-**-**.us-**.compute.internal   None          ec2-**-**-**-**.us-**.compute.amazonaws.com    QTP-Ops-03                                               
i-0ad**************  stopped  t2.micro    **.**.**.**   ip-**-**-**-**.us-**.compute.internal   None          ec2-**-**-**-**.us-**.compute.amazonaws.com    QTP-Ops-04                                              
i-032**************  running  t3a.large   **.**.**.**   ip-**-**-**-**.us-**.compute.internal   **.**.**.**   ec2-**-**-**-**.us-**.compute.amazonaws.com    QTP-Ops-02
i-095**************  running  t3a.xlarge  **.**.**.**   ip-**-**-**-**.us-**.compute.internal   **.**.**.**   ec2-**-**-**-**.us-**.compute.amazonaws.com    QTP-Mds-01
```
# IAM Access Analyzer quotas<a name="access-analyzer-quotas"></a>

IAM Access Analyzer has the following quotas:


| Resource | Default quota | Maximum quota | 
| --- | --- | --- | 
|  Maximum analyzers with an account zone of trust  |  1  |  1  | 
|  Maximum analyzers with an organization zone of trust  |  5  |  20¹  | 
|  Maximum archive rules per analyzer  |  100 Each archive rule can have up to 20 values per criterion\.  |  1,000¹  | 
| Maximum number of access previews per analyzer per hour | 1,000 | 1,000 | 
| AWS CloudTrail log files processed per policy generations | 100,000 | 100,000 | 
| Concurrent policy generations | 1 | 1 | 
| Policy generation AWS CloudTrail data size | 25 GB | 25 GB | 
| Policy generation AWS CloudTrail time range | 90 days | 90 days | 
| Policy generations per day |  Africa \(Cape Town\): 5 Asia Pacific \(Hong Kong\): 5  Europe \(Milan\): 5 Middle East \(Bahrain\): 5 All other supported regions: 50  Canceled policy generation requests apply to the daily quota\.   | Africa \(Cape Town\): 5 Asia Pacific \(Hong Kong\): 5  Europe \(Milan\): 5 Middle East \(Bahrain\): 5 All other supported regions: 50 | 

¹Some quotas are customer\-configurable using [Service Quotas](https://docs.aws.amazon.com/servicequotas/latest/userguide/intro.html)\.
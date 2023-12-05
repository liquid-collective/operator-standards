## Developing an Ethereum Node Operator Performance Methodology

To address the current gap in standardized benchmarking for Ethereum validators, Liquid Collective introduces the first phase of an open methodology for evaluating node operator performance. Built on the [Rated Validator Effectiveness Rating (RAVER)](https://docs.rated.network/methodologies/ethereum-beacon-chain/rated-effectiveness-rating) developed by [Rated Labs](http://rated.network/home), this framework is designed to provide an objective tool for assessing whether an Ethereum node operator maintains a standard of enterprise-grade validator performance. 


This methodology is a step toward creating widely accepted node operator (NO) performance and risk standards within the Ethereum ecosystem. It offers a consistent framework for benchmarking, aiming to bring clarity and uniformity to the evaluation of NO performance. 

We encourage the community to use this open methodology to foster a more transparent and standardized approach to performance assessment of NOs across the Ethereum network.

You can learn more about the Node Operator Performance & Risk Standards initiative in the [repository’s introduction](operator-standards/README.md). To provide input or feedback on this methodology, please open an Issue in the repository [here](https://github.com/liquid-collective/protocol-standards/issues), or, use [this form](https://docs.google.com/forms/d/e/1FAIpQLScVkbYCY819fahbu9NsgLUozlcNPcuJ52zxaZ5w0PH-Qa_sUg/viewform) 

<br />

### Objectives of the Performance Measurement and Monitoring Methodology 

<b>Establishing objective performance metrics</b>
<ul>
<li><b>Purpose</b>: To define a set of clear, quantifiable metrics that accurately describe the performance of a NO’s validator fleet and their individual validator keys within and across active sets.</li>
<li><b>Implementation Considerations</b>: These metrics should be deterministic, reduce randomness and cover key aspects of validator performance, such as block proposal and participation in consensus processes, providing a detailed picture of NO effectiveness.</li>
</ul>

<b>Developing an open, community-driven methodology</b>
<ul>
<li><b>Purpose</b>: To craft a transparent and publicly accessible methodology for the ecosystem, enabling comparative assessments and fostering collaborative, community-driven methodology improvements.</li>
<li><b>Implementation Considerations</b>: This methodology will be documented in a user-friendly way, encouraging adaptations from builders and professionals for ongoing refinement and collaborative improvement.</ul>
</ul>


### Design principles for the methodology

<b>Maximizing validator performance within operational constraints</b>
<ul>
<li><b>Focus</b>: This approach concentrates on optimizing validator performance in terms of consensus layer and execution layer rewards, while considering the following constraints.</li>
<li><b>Constraints</b>:</li>
<ul> 
<li><b>Replicability and auditability</b>: Designed to be independently replicated and audited,  the methodology will include detailed procedures and criteria, and verifiable, accessible data sources, reinforcing transparency and trust in the performance assessments.</li>
<li><b>Reducing randomness in performance evaluation</b>: To minimize the impact of random factors in the performance evaluation, methods to isolate and account for non-deterministic (outside of an operator’s control) variables including network conditions and execution layer rewards will be developed, helping ensure the evaluations are as fair and accurate as possible.</li>
<li><b>Accessibility and comprehensibility</b>: Ensuring that the methodology is comprehensible to a technically-inclined audience, clear and explanatory documentation will be provided where necessary.</li>
</ul>
</ul> 

Moreover, while not an explicit constraint of the performance methodology design goals per se, paired with the soon to be [proposed risk framework](/risk-nodeoperators/README.md), the performance methodology should promote a balance that discourages operators from pursuing performance improvements that exceed an acceptable level of risk, defining clear risk parameters to be incorporated into the NO evaluation process. 

<br />
<br />  

> [!NOTE]
> <b>A note on risk</b> 
> <br />
> As noted in the design principles above, to adjust NO performance expectations for an acceptable risk tolerance it is crucial to establish a risk threshold, and then to optimize these performance metrics within that constraint. 
>
> NOs play an important role in the security and performance of the protocol. There is a clear need for robust operational controls and processes to maintain enterprise-grade security and performance standards. As such, performance must be assessed through a [risk-adjusted lens](https://alluvial.finance/risk-adjusted-reward/), evaluating the potential reward of participation in consideration of the degree of risk that must be accepted to achieve it.
>
> Members from Rated Labs and Alluvial with input from Liquid Collective’s NOs, Figment, Coinbase Cloud, and Staked, are actively working on an open risk evaluation and benchmarking methodology as part of this NO Standards initiative—one that can be used to objectively determine if a node operator maintains an enterprise-grade standard for security, infrastructure, and other relevant risk categories. The risk methodology will be published [in the repository](/risk-nodeoperators/README.md) in the near future for community feedback.
> <br />
<br />

## Performance Methodology: Background

### Research, designs, and approach

Starting out, we defined 3 different approaches that we would explore in terms of crafting a performance methodology for the Liquid Collective active set: 
<ol>
<li>A spec based deterministic approach.</li>
<li>A rate of return approach.</li>
<li>An opportunity cost benchmarking approach.</li>
</ol>

### Defining metrics

We then proceeded to define metrics for each of those approaches:
<ul>
<li><b>Spec based</b>: for this approach we selected the Rated Validator Effectiveness Rating (RAVER) as the vehicle. The RAVER is a measurement of the “job completion rate” of a validator (and collections of validators bound together by agency i.e. an operator) in terms of the deterministic duties they are asked to perform by the protocol. You can learn more about it at <a href="https://docs.rated.network/methodologies/ethereum-beacon-chain/rated-effectiveness-rating" target="_blank">docs.rated.network</a>.</li>
<li><b>Rate of return</b>: for this approach we selected gross rewards earned (EL + CL) and APR% benchmarking as the tools of choice. You can learn more about how we compute <a href="https://docs.rated.network/methodologies/ethereum-beacon-chain/backward-looking-apr" target="_blank">APR% here</a>.</li>
<li><b>Opportunity cost</b>: for this approach, we defined performance measurement via opportunity cost, as the delta between rewards achieved and the theoretical maximum of a validator’s (and thereafter an operator’s) rewards earning potential. We selected 3 different ways to measure opportunity cost, that progressively expand in terms of what the scope of “maximum rewards'' is defined as:</li>
<ul>
<li>Oppcost1: all CL rewards except proposals</li>
<li>Oppcost2: all CL rewards including proposals</li>
<li>Oppcost3: all CL AND EL rewards</li>
</ul>
</ul>

We ran extensive analyses on data spanning back to the Beacon Chain genesis block. We present an abbreviated version of those findings below:
<ul>
<li><b>Result 1</b>: Rewards on post-merge Ethereum are stochastic/random on aggregate. While CL rewards are nearly perfectly deterministic, EL rewards are random (see <a href="https://gist.github.com/RplusT/56e4f5335cf72fa389c5424367ecf745" target="_blank">here</a> for an illustrative analysis). The sum of the two parts (gross rewards) is as random as its most random end; thereby is stochastic/random overall.</li>
<li><b>Result 2</b>: Consensus layer rewards are nearly perfectly deterministic As expected, CL rewards are very tightly distributed and correlate ~99% with the hit-rate that validators and validator operators exhibit in terms of the duties they are tasked to perform.</li>
<li><b>Result 3</b>: According to the design goals set, the RAVER and oppcost2 (the best measure of opportunity cost benchmarking) were shortlisted as the best performance metrics. The two metrics were found to be correlated to the tune of ~98%. This is expected as they largely track the same source material from two different vantage points; top-down (oppcost2) and bottom-up (RAVER). The main difference is that the RAVER does not capture sync committee duties (this is so by design, so as to remove the “randomness” and advantage of operation size in the sync committee selection process).</li>
</ul>

<br/>

## The Performance Methodology 

Given the above, we proposed a layered performance methodology that captures the deterministic elements of NO performance at the consensus and execution layers of operation, separately. We proposed (i) the Rated Validator Effectiveness Rating (hereon RAVER) as the measure of performance for the CL, and (ii) a target rate for successful proposals, at the operator level.

<br/>

<table>
<tr>
<th>METRIC &#128073;</th>
<th>RAVER (Rated Validator Effectiveness Rating)</th>
<th>Missed block quota</th>
</tr>
<tr>
<td>WHAT IT’S GOOD FOR &#128073;</td>
<td>Ongoing performance and SLA monitoring and benchmarking.</td>
<td>Ongoing performance and SLA monitoring and benchmarking.</td>
</tr>
<tr>
<td>OPERATION LAYER &#128073;</td>
<td>CONSENSUS LAYER</td>
<td>EXECUTION LAYER</td>
</table>

<br/>
    

> [!NOTE]
> We selected the RAVER over oppcost2 as the metric of choice to define deterministic performance. While the two are very highly correlated, the RAVER offers some clear advantages as an “interface”, namely: 
> <ol>
> <li>The RAVER more densely packs information, and offers better granularity than oppcost2 in terms of observability (e.g. The RAVER surfaces more clusters of an operator in a fleet-wide histogram).</li>
> <li>The RAVER is already well adopted by operators via the Rated Network Explorer and a more familiar interface.</li>
> <li>The RAVER does not include sync committee participation, which introduces noise into the metric definition.</li>
> </ol>
<br/>
<br/>

### The RAVER

The Rated Validator Effectiveness Rating (RAVER) is a measure of how well a validator has been performing its deterministic duties over time.

An Ethereum validator’s performance is largely described by its attestation and block proposal duties and responsibilities to the network. As such, attester effectiveness and proposer effectiveness are the key components of the RAVER. Essentially, it is a unified effectiveness rating that combines attester and proposer effectiveness. 

> <div style="text-align: center;">
> RAVER == [3/8 * proposer_effectiveness] + [5/8 * attester_effectiveness]
> </div>


#### Attester effectiveness

Validators are called to attest once in every epoch. These attestations are important consensus material. When attesting, validators vote on their version of the perceived state of the chain, which is described by a handful of distinct variables. When validators perform their duties appropriately, they earn rewards; if they do not, they are penalized. For more information on the core duties related to attestations and the calculation of attester effectiveness, please refer to Rated’s documentation [here](https://docs.rated.network/methodologies/ethereum-beacon-chain/rated-effectiveness-rating).


#### Proposer effectiveness

A block proposer is a validator that is chosen to pack the attestation information together and commit the block to the chain. There is one proposer per slot and 32 per epoch. Given their work is critical, the reward that they earn for successfully proposing a block is disproportionate to any given attester’s reward in an epoch.

Being elected as a proposer has a much lower probability attached to it (<i>32/active Ethereum validators</i>), compared to a validator’s attestation duties (which is 100%). 

For more information on the computation of the RAVER, please refer to Rated’s documentation [here](https://docs.rated.network/methodologies/ethereum-beacon-chain/rated-effectiveness-rating/effectiveness-rating).


### Missed blocks quota

At a high enough level, all missed rewards on the Ethereum execution layer stem from missing block proposals. Given the lower probability of proposing and the random extreme distribution of rewards, missing a block proposal can have adverse effects on the return profile of node operators, and the protocol as a whole thereafter.

In order to capture the outsized effect a large number of missed blocks could have on the protocol's competitiveness, we introduce the notion of a maximum allowed percentage of missed blocks any given operator is allowed to miss, in a given time period. This is computed as the sum of missed proposals, divided by the number of proposal slots a given operator was allotted by the protocol.

Importantly, though, it should be noted that the recommendation is that proposals that are missed by no fault of the operator (e.g. a MEV Relay unblinding the payload late) should not be included in the tally. Agency might be tricky to attribute in some cases (e.g. a bug with a recent client release, but the operator having not tested the release or upgraded too early), and as such we encourage taking an iterative approach in dictionary-building for the various permutations of these cases.

<i>The methodology and benchmark for missed blocks quota are still being evaluated. The evaluation phase will be followed by an outreach for feedback from the Ethereum community and members of the Liquid Collective.</i>

<br/>

## Benchmarking

In this section we discuss the methodology for setting the acceptable lower bounds for a Liquid Collective NO’s performance. The ultimate goal here is to power an SLA between the protocol and its operators. 

Given that the protocol’s active set is composed of professional operators, we needed a relevant benchmark value that reflects the expected performance of enterprise grade operators over time.  

The metric we chose is <b>the aggregate RAVER for operators with more than 100 validator keys under management</b>. The per operator RAVER value is aggregated by checking the fulfillment of the duties of the operator validator set at the duty level itself, and not aggregated at the validator level. Specifically this entails getting all the duties of the validators for a given operator, assessing the correctness and effectiveness of each duty, and finally calculating the RAVER for the operator. This is in contrast to calculating the RAVER per validator and getting the average of these RAVER values to come up with an operator’s performance measure. 

By computing an operator’s performance at the duty level itself, the methodology avoids a select few validators disproportionately affecting the operator’s RAVER (i.e. “average of averages”). This also ensures that the measure of performance is not influenced by the length of time certain validators have been active (or inactive) in an operator’s set.

### RAVER benchmark

To successfully evaluate NOs in the active set we had to define the RAVER benchmark. The benchmark is defined as a 3 month rolling value and will be recalculated every month as the median RAVER for Ethereum NOs running 100 or more validators minus one standard deviation. 

This initial benchmark was determined through extensive analysis of performance data, over several months. In the analysis we observed that particularly in the set of large(er) operators, the distribution of performance over quarterly timeframes has low variance (i.e. is concentrated around the mean), deeming “binning by percentile” an approach too sensitive (e.g. the performance of an operator at the 30th percentile and another at the 70th percentile were often found to be only a few percentage points apart).

In order to then avoid being overly punitive to NOs, we decided to set the initial benchmark at the 50th percentile (or the median RAVER) minus one standard deviation. 

<br/>
<br/>
<figure>
    <img src="/performance-nodeoperators/Images/2023-performance-1.png"
         alt="Probability density function illustrating how performance via RAVER is distributed for large(er) operators."
         width="750">
    <figcaption><i>The above probability density function is an illustration of how performance via RAVER is distributed for large(er) operators. The purple shaded area represents “sub-par” performance as defined by the selected benchmark.</i></figcaption>
</figure>
<br/>
<br/>

This adjustment is designed to prevent the penalization of NOs for minor performance dips below the benchmark, especially considering the tight correlation observed around the median RAVER. As we make progress in defining risk standards for NOs and deepen our understanding of how various risk categories and  risk mitigation strategies impact their performance, we will make further adjustments.

The benchmark methodology will be reviewed by the Liquid Collective every 3 months in order to make any necessary adjustments based on further analysis of performance and risk metrics and to best reflect enterprise-grade performance requirements and the state of the network.

### Application of the methodology: SLAs and Node Operators credit calculation 

As one example of how the methodology and benchmark can be practically applied, Liquid Collective will use the methodology to monitor the performance of the protocol’s NO active set against the rolling benchmark, and will establish service level agreements (SLAs) between NOs and the protocol, establishing a baseline commitments to performance compared to peers.  

To incentivize performance above the Benchmark, NOs will need to credit the protocol if they underperform over a predetermined period of time. The credits owed by node operators are calculated in the following way.

#### Formula
<ul>
<li><b>B<sub>t</sub></b> = Benchmark for a given time period. The benchmark is a 3 month rolling value and is calculated every month as the median RAVER for NOs running 100 or more validators minus one standard deviation.  </li>
<li><b>R<sub>NOt</sub></b> = node operator RAVER for a given time period.  </li>
<li><b>MCLPR<sub>t</sub></b> = Missed consensus layer rewards per 1% decrease in RAVER per validator index for a given time period.This is calculated by first deriving the average missed CL reward for all validators across the network (missed attestation rewards + missed CL proposer rewards) and then running a linear regression between RAVER and missed CL rewards to derive the relationship between the change in RAVER and missed CL rewards for a given period.  </li>
<li><b>VC<sub>NOt</sub></b> = Validator count of node operator in a given time period.  </li>
<li><b>E<sub>At</sub> / E<sub>AMt</sub></b> = Active validator multiplier to adjust for time a validator has been active for a given time period where  </li>
<ul>
<li><b>E<sub>At</sub></b> = Actual epochs active for a node operator’s validator set in a given time period </li> 
<li>&emsp;&emsp;<b>E<sub>AMt</sub></b> = Max possible epochs active for a node operator’s validator set for a given time period  </li>
</ul>
<li><b>NOC</b> = Node Operator Credits</li>
</ul>

<br/>

> <div style="text-align: center;">
> 
> When R<sub>NOt</sub> < B<sub>t</sub> ;
>
> <i>NOC = (B<sub>t</sub> - R<sub>NOt</sub>) * MCLPR<sub>t</sub> * VC<sub>NOt</sub> * (E<sub>At</sub> /E<sub>AMt</sub>)</i>
> 
> Else, <i>NOC = 0</i>
>
> </div>

<br/>

<h4><i>B<sub>t</sub> - R<sub>NOt</sub></i></h4>

The credit calculation for an underperforming node operator (R<sub>NOt</sub> < B<sub>t</sub>) is calculated first by taking the difference in percentage points between the relevant benchmark (B<sub>t</sub>) and the node operator’s performance in terms of its average RAVER in the same relevant time period (R<sub>NOt</sub>). The average RAVER for a node operator is calculated by checking the fulfillment of the duties of its validator set at the <i>duty level itself</i>, and not aggregated at the validator level. This ensures that the measure of performance is not influenced by the length of time certain validators have been active (or inactive) in an operator’s set.
  
<h4><i>MCLPR<sub>t</sub>*VC<sub>NOt</sub></i></h4>

The difference between the benchmark and the node operator’s RAVER is then multiplied by the corresponding missed consensus rewards per 1% decrease in RAVER. The reasoning here is that every percentage point decrease in performance has a corresponding value in terms of rewards not being realized by a node operator through its validator set (i.e. missed rewards). 

For more information on how missed rewards are calculated, see [here](https://docs.rated.network/methodologies/ethereum-beacon-chain/penalties-and-missed-rewards/validator-missed-rewards-computation/consensus-missed-rewards-computation). Given that the RAVER is a measure of how well a validator performs based on its duties to the specifications of the Ethereum Beacon Chain protocol (i.e. the consensus layer), there is a strong correlation between this metric and the rewards an underperforming validator (i.e. not fulfilling its duties) fails to receive. Rated Labs ran a regression analysis on this based on Q2 2023 data [here](https://gist.github.com/RplusT/ef66827a78c574a7179261d5c69107b3). The MCLPR<sub>t</sub> can be calculated every time the B<sub>t</sub> is set. We then multiply this by the maximum number of validators controlled by the operator during the time period (VC<sub>NO</sub>).

<h4><i>(EAt /EAMt)</i></h4>
Since the MCLPR<sub>t</sub> is a metric derived at the validator level, we have to re-modulate the rewards calculation at the duty level to be consistent with the node operator RAVER calculation. Recall that the RAVER is calculated at the duty level to ensure it is not affected by a validator’s activation time. Given this, the modulation is done by using the proportion of the total epochs a node operator’s validator set is active in the time period (E<sub>At</sub>) versus the maximum possible epochs the same validator set could have been active (E<sub>AMt</sub>). Epochs are used here since duties are assigned by the protocol every epoch. In other words, E<sub>At</sub> is the summation of each individual validator’s number of active epochs and E<sub>AMt</sub> is the number of epochs in the time period multiplied by validators controlled by the operator (VC<sub>NOt</sub>).

<br/>

<h4><i>Example:</i></h4>  
We are in Q3, 2023. On Sept 1st we are going to evaluate the theoretical Liquid Collective Node Operator 1 for the month of August.    

<br/>

Data for Node Operator 1 
  
<br/>

<table>
<tr>
<td>RAVER 50th percentile</td>
<td>One standard deviation</td>
<td>Q2 Benchmark</td>
<td>Total validator count</td>
<td>NO August RAVER</td>
<td>NO Count of Validators active from August 1 - 31</td>
<td>NO Count of Validators active only from August 21 - 31</td>
</tr>
<tr>
<td>97%</td>
<td>1%</td>
<td>96%</td>
<td>10</td>
<td>95%</td>
<td>1000</td>
<td>10</td>
</table>

<br/>

#### Calculation of credits  

<b>B<sub>t</sub></b> = 96%  
<b>R<sub>NOt</sub></b> = 95%  
<b>MCLPR<sub>t</sub></b> = 0.002 ETH  
<b>VC<sub>NOt</sub></b> = 1,010  
<b>E<sub>AMt</sub></b> = 1,010 * 225 epochs * 31 days = 7,044,750  
<b>E<sub>At</sub></b> = (1,000 * 225 epochs * 31 days) + (10 * 225 epochs * 11 days) = 6,999,750  
  <br/>
<b>NOC</b> = (B<sub>t</sub> - R<sub>NOt</sub>) * MCLPR<sub>t</sub> * VC<sub>NOt</sub> * (E<sub>At</sub> / E<sub>AMt</sub>)
NOC = (96 - 95) * 0.002 ETH * 1,010 * (6,999,750 / 7,044,750)  
NOC = 0.002 ETH * 1,010 * 0.9936  
<b>NOC = 2.007 ETH</b>  
  <br/>
Based on August’s performance, Node Operator 1 will owe 2.007 ETH to the Liquid Collective protocol.
<br/>
<br/>

### Liquid Collective’s Node Operator Working Group

To validate our findings and improve the performance methodology, a working group was formed with members from <b>[Rated Labs](https://www.rated.network/home), [Alluvial](https://alluvial.finance/), [Figment](https://figment.io/), [Coinbase Cloud](https://www.coinbase.com/cloud), and [Staked](https://staked.us/)</b>. It was important to engage and collaborate with leading NOs in the space to help shape and validate the methodologies and evaluation processes. The working group multiple times to hear presentations, provide feedback, debate, improve, and align behind the methodologies and respective benchmarks. 

<br/>

## What's next

It is important that we continue to enhance the performance methodology to more accurately reflect validator performance, evolving customer requirements, and the network’s state. Our roadmap includes the following methodology improvements:
<ul>
<li><b>Missed blocks quota</b>: Finalize the missed blocks quota methodology and benchmark in the context of the working group and feedback from Liquid Collective members and the community. </li>
<li><b>Accounting for slashings</b>: The RAVER incorporates slashing penalties in a roundabout manner; it takes into account all the penalties a validator has accrued by being active but not attesting, since the slashing proof was included onchain. This makes a material difference for a single validator, but the signal gets drowned out as the validator set increases (assuming all other validators in the set were not slashed and performant), becoming barely visible in large numbers.</li>
<li><b>APIs and dashboards</b>: Offering full transparency into the performance and security of NOs to end users of the protocol and stakeholders necessitates the availability of adequate metrics, exposed via standardized APIs and comprehensive dashboards.</li>
<li><b>DVT</b>: build a model to evaluate optimal DV cluster configurations for Liquid Collective’s active set and measure DV performance against established performance and risk benchmarks, before deploying DVT on mainnet.</li>  
</ul>
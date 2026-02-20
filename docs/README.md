# GA4: a practical guide for content designers

## Purpose of this guide
This guide gives content designers at every level the practical knowledge to get started with GA4 (Google Analytics 4). You'll learn how to navigate the interface and create customised reports that inform your content decisions and support hypothesis testing.

At first glance, GA4 is cluttered with generic pre-built reports and features aimed broadly at the e-commerce world. For a content designer (especially one in public service) this can understandably feel irrelevant and off-putting. This guide helps you to quickly find what’s most useful for content design, and safely bypass the rest.

The default GA4 setup is the free tier without customised tracking configured. If your organisation or team has implemented any custom tracking, this will extend the possibilities but share the same foundation.

## Why GA4 is critical for content design
GA4 provides insights into user behaviour and needs at scale. The data represents the majority of our users, interacting with your content in a real world context rather than a controlled research setting. It’s a critical aid to formulating effective design hypotheses and questions to explore further in user research. Broadly speaking, analytics data can tell you what is happening, while user research can help you to explore why.

It’s important for content designers to be confident accessing and analysing web metrics directly. Without firsthand analysis of web metrics, the profession risks:
- incomplete understanding of real world user behaviour that’s taking place outside of controlled research settings
- limited ability to empirically demonstrate the effectiveness of design changes or the benefits of content design at scale
- over-reliance on the small sample sizes in user research that are more vulnerable to distortion
- reliance on peers in other professions to source, package or interpret user data, limiting the precision or depth of design insights
- reduced ability to influence design decisions and persuade stakeholders with a data-driven approach
- difficulty auditing and benchmarking any existing content in a discovery phase, reinforcing the misconception that content designers aren’t needed until alpha
- wastefully collecting user data that isn’t being acted upon


### Common misconceptions

#### GA4 data is too heavily sampled and overly reliant on cookie consent to provide reliable insights.
[Data sampling](https://support.google.com/analytics/answer/13331292?hl=en) (estimating total numbers from a smaller subset of data) is only applied in GA4’s free tier once a report exceeds 10 million ['events'](https://support.google.com/analytics/answer/9322688?hl=en) (specific interactions or occurrences), at which point the data will be statistically very significant. GA4 also introduced [‘cookieless measurement’](https://support.google.com/analytics/answer/10089681?hl=en), reducing the impact of cookie consent rates. Even with both considerations, the number of users represented in GA4 data will far exceed what’s feasible in user research (on which basis we routinely make important design decisions).

#### Web analytics is the domain of performance analysts, not content designers.
Even if you’re fortunate enough to have a dedicated performance analyst on your team, content design will not be their focus. Content designers are best placed to identify and monitor the granular metrics that directly inform day-to-day content design decisions (as opposed to strategic performance data, frameworks or dashboards that serve the whole team). Relying exclusively on the availability of a performance analyst risks missing valuable insights that are essential for content improvement.

#### My team’s product manager / delivery manager / business analyst is great with GA4 and shares the relevant data.
Each profession will use GA4 in a different way. It’s important to be empowered to directly ask your own in-depth questions of the data – questions that are aligned with content design goals and granular user behaviours, rather than overall product performance or management information.

#### GA4 doesn’t really tell us anything useful, we get the most valuable insights from user research.
The more deeply you understand and can explore GA4 data, the more valuable you’ll find the insights. Unless no GA4 data is being gathered (in discovery or alpha phases, for instance), analytics and user research should always complement one another. There’s no substitute for the scale and real-world insights that analytics provide. Analytics can inform where to focus user research for the most impact, and can validate research findings by connecting them to broader trends. Together, they offer a complete picture to guide effective content design.

#### We shouldn’t use GA4 because it does not respect data privacy.
GA4 provides significantly improved data privacy controls over UA (Universal Analytics, the previous version). Your GA4 admin can easily disable ‘Google signals data collection’ and ‘Advanced settings to allow for ads personalisation’ (both in Admin > Property settings > Data collection and modification > Data collection). They can also turn off all ‘Data Sharing Settings’ (Admin > Account settings > Account details). Your team should always ensure that URLs, URL parameters and page titles do not contain personally identifiable information (PII). See [Best practices to avoid sending Personally Identifiable Information (PII)](https://support.google.com/analytics/answer/6366371?hl=en).

#### GA4 is too impenetrable for content designers to have time for.
The GA4 interface can be off-putting at first. But once you know which features aren’t relevant to content design, it’s quite straightforward to self-serve. That’s where this guide is here to help.

## The case for trunk based development

+ No one likes merging
+ Everyone works on ‘master’
+ Changes regularly pushed back to origin

Note: Reminder: opinion follows  
  Still get conflicts but they are incremental, allowing you to change your approach—possibly backing off from changing conflicting areas.  

--

## Handling multiple changes in progress

+ Feature Toggles hide incomplete features in production
+ AKA Feature Shields/Flags/Switches/Flippers
+ Conditionals around bits of code/user interfaces
+ May be toggled on and off per environment
+ (see Further Reading for a good [Feature Toggles article](https://martinfowler.com/articles/feature-toggles.html))

--

## Trunk Development + CI == 👍

+ Changes to trunk always picked up by CI system
+ Feature changes are continuously integrated with each other
+ You *can* toggle features on per environment or per test
+ If you do, feature is tested on each push
+ Increased complexity—introduces a new code path
+ May need to run tests with multiple toggle combinations

Note: It is possible to do CI with branches but some organisations typical build process or CI tooling means they don’t.
  Testing features in isolation on branches is not CI.    
  Features promoted or new builds toggle per environment.  
  Feature branches don’t address complexity—can’t test integrated WIP.  

---

## Implementing a Feature Toggle

```javascript
  const features = fetchFeatureTogglesFromSomewhere();

  function generateInvoiceEmail(){
    const baseEmail = buildEmailForInvoice(this.invoice);
    if( features.isEnabled("next-gen-ecomm") ){ 
      return addOrderCancellationContentToEmail(baseEmail);
    }else{
      return baseEmail;
    }
  }
```

Taken from [Feature Toggles (aka Feature Flags)](https://martinfowler.com/articles/feature-toggles.html)

--

## Tidying Up

Code was added to implement feature toggles so we need to tidy this away once functionality fully released

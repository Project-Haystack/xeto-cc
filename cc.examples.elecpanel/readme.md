## Introduction

This library defines a Xeto device spec for an example electric panelboard.

Panelboards can be configured in many different ways.  In this example core concepts are introduced to help give system integrators the understanding they need to develop specs for their own project specific panelboards.

Also, the purpose of this example is to help drive discussion within the Project Haystack community on how we may improve the related data models.  Therefore, these specs are preliminary, subject to change and shall not be used for construction.

## Panel example

The goal of this example is to describe the semantics necessary to construct the one-line diagram below using a Project Haystack data model.

<img src="panel.png" width="350" height="210" />

## Notes

 * Need to decide if it makes sense to have both `ElecAcRatedMaxContinuousCurrentAttr` and `ElecAcRatedContinuousCapacityCurrentAttr`.
 * Might want to change `ElecAcRatedMaxContinuousCurrentAttr` to `ElecAcRatedInputMaxContinuousCurrentAttr` to have consistency with `ElecAcRatedInputMaxCurrentAttr`.
 * Not sure if the max continuous rating attr should be applied to the electrical bus.
 * Might want to change `ElecAcRatedInputMaxCurrentAttr` to `ElecAcRatedMaxCurrentAttr` to describe the rating for an electrical bus.
 * Need to determine if elec bus equip entity should describe a neutral or not (if applicable)
 * Need to update attrs to clarify the ratings are based on RMS ratings (if applicable)

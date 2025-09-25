<!-- loio924f892e67b7443fbb4476b3e81959b2 -->

# Upgrade a Service Plan

Upgrade your SAP AI Core service instance from the Free plan to a Standard or Extended plan while keeping your data and models.



<a name="loio924f892e67b7443fbb4476b3e81959b2__context_s4t_fnn_lgc"/>

## Context

You can upgrade your SAP AI Core service instance from the Free plan to a Standard or Extended plan.

During the upgrade, your metadata and transaction data \(including trained models\) are retained.

You can also upgrade from the Standard plan to the Extended plan.

> ### Restriction:  
> Downgrading from an Extended or Standard plan to the Free plan is not supported.
> 
> Downgrading from the Extended plan to the Standard plan is not supported.
> 
> If a Standard or Extended instance is deleted, you cannot create a new Standard plan instance.



<a name="loio924f892e67b7443fbb4476b3e81959b2__steps_qtp_xmn_15b"/>

## Procedure

1.  Open your global account in the SAP BTP cockpit.

2.  Go to your subaccount.

3.  In the navigation area, choose *Instances and Subscriptions*.

4.  Search for SAP AI Core.

5.  At the end of the subscription row, select the ellipsis \(…\) and choose *Update*.

    ![](images/upgrade_free_tier_27775d6.jpg)

6.  In the wizard that opens, select *default* and click *Update Subscription*.




<a name="loio924f892e67b7443fbb4476b3e81959b2__result_yjn_tnn_lgc"/>

## Results

After you have updated your service plan, free plan restrictions no longer apply.

All data from your Free plan is migrated automatically to your new plan.

User permissions remain unchanged.


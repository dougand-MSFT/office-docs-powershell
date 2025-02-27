---
external help file: Microsoft.Open.Teams.CommonLibrary.dll-Help.xml
Module Name: MicrosoftTeams
online version: https://docs.microsoft.com/powershell/module/teams/get-csphonenumberassignment
applicable: Microsoft Teams
author: jenstrier
ms.author: jenstr
ms.reviewer: 
manager:
schema: 2.0.0
---

# Get-CsPhoneNumberAssignment

## SYNOPSIS
This cmdlet displays information about one or more phone numbers.

> [!NOTE]
> **Preview** The use of this cmdlet is in Public Preview.

## SYNTAX

### Assignment (Default)
```powershell
Get-CsPhoneNumberAssignment [-ActivationState <string>] [-AssignedPstnTargetId <string>] [-CapabilitiesContain <string>]
	[-CivicAddressId <string>] [-IsoCountryCode <string>] [-LocationId <string>] [-NumberType <string>]
	[-PstnAssignmentStatus <string>] [-Skip <int>] [-TelephoneNumber <string>] [-TelephoneNumberContain <string>]
	[-TelephoneNumberGreaterThan <string>] [-TelephoneNumberLessThan <string>] [-TelephoneNumberStartsWith <string>] [-Top <int>]
	[<CommonParameters>]
```

## DESCRIPTION
This cmdlet displays information about one or more phone numbers. You can filter the phone numbers to return by using different parameters.

Returned results are sorted by TelephoneNumber in ascending order.

## EXAMPLES

### Example 1
```powershell
Get-CsPhoneNumberAssignment -TelephoneNumber +12065551234
```
```output
TelephoneNumber         : +12065551234
NumberType              : CallingPlan
ActivationState         : Activated
AssignedPstnTargetId    : dc13d97b-7897-494e-bc28-6b469bf7a70e
Capability              : {UserAssignment}
CivicAddressId          : 703b30e5-dbdd-4132-9809-4c6160a6acc7
IsoCountryCode          : US
LocationId              : 407c17ae-8c41-431e-894a-38787c682f68
LocationUpdateSupported : True
PortInOrderStatus       : 
PstnAssignmentStatus    : UserAssigned
PstnPartnerId           : 7fc2f2eb-89aa-41d7-93de-73d015d22ff0
PstnPartnerName         : Microsoft
```
This example displays information about the Microsoft Calling Plan subscriber phone number +1 (206) 555-1234. You can see that it is assigned to a user.

### Example 2
```powershell
Get-CsPhoneNumberAssignment -TelephoneNumber "+12065551000;ext=524"
```
```output
TelephoneNumber         : +12065551000;ext=524
NumberType              : DirectRouting
ActivationState         : Activated
AssignedPstnTargetId    : 2713551e-ed63-415d-9175-fc4ff825a0be
Capability              : {ConferenceAssignment, VoiceApplicationAssignment, UserAssignment}
CivicAddressId          : 00000000-0000-0000-0000-000000000000
IsoCountryCode          : 
LocationId              : 00000000-0000-0000-0000-000000000000
LocationUpdateSupported : True
PortInOrderStatus       : 
PstnAssignmentStatus    : UserAssigned
PstnPartnerId           : 
PstnPartnerName         : 
```
This example displays information about the Direct Routing phone number +1 (206) 555-1000;ext=524. You can see that it is assigned to a user.

### Example 3
```powershell
Get-CsPhoneNumberAssignment -CapabilitiesContain "VoiceApplicationAssignment,ConferenceAssignment"
```
This example returns all phone numbers that have both the capability VoiceApplicationAssignment and the capability ConferenceAssignment assigned, but phone numbers that have
only one of these capabilities assigned won't be returned.

### Example 4
```powershell
Get-CsPhoneNumberAssignment -AssignedPstnTargetId user1@contoso.com
```
This example returns information about the phone number assigned to user1@contoso.com.

### Example 5
```powershell
Get-CsPhoneNumberAssignment -AssignedPstnTargetId aa1@contoso.com
```
This example returns information about the phone number assigned to resource account aa1@contoso.com.

### Example 6
```powershell
Get-CsPhoneNumberAssignment -ActivationState Activated -CapabilitiesContain VoiceApplicationAssignment -PstnAssignmentStatus Unassigned
```
This example returns information about all activated phone numbers with the capability VoiceApplicationAssignment that are not assigned.

## PARAMETERS

### -ActivationState
Filters the returned results based on the number type. Supported values are Activated, AssignmentPending, AssignmentFailed, UpdatePending, and UpdateFailed.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AssignedPstnTargetId
Filters the returned results based on the user or resource account ID the phone number is assigned to. Supported values are UserPrincipalName, SIP address, and ObjectId.


```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CapabilitiesContain
Filters the returned results based on the capabilities assigned to the phone number. You can specify one or more capabilities delimited by a comma. Supported capabilities

are ConferenceAssignment, VoiceApplicationAssignment, UserAssignment, and OCMobile.


If you specify only one capability, you will get all phone numbers returned that have that capability assigned. If you specify a comma separated list for instance like 
ConferenceAssignment, VoiceApplicationAssignment you will get all phone numbers that have both capabilities assigned, but you won't get phone numbers that have only
VoiceApplicationAssignment or ConferenceAssignment assigned as capability.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CivicAddressId
Filters the returned results based on the CivicAddressId assigned to the phone number. You can get the CivicAddressId by using [Get-CsOnlineLisCivicAddress](/powershell/module/skype/get-csonlineliscivicaddress).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IsoCountryCode
Filters the returned results based on the ISO 3166-1 Alpha-2 contry code assigned to the phone number.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LocationId
Filters the returned results based on the LocationId assigned to the phone number. You can get the LocationId by using [Get-CsOnlineLisLocation](/powershell/module/skype/get-csonlinelislocation).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NumberType
Filters the returned results based on the number type. Supported values are DirectRouting, CallingPlan, and OperatorConnect.


```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PstnAssignmentStatus
Filters the returned results based on the assignment status. Support values are Unassigned, UserAssigned, ConferenceAssigned, VoiceApplicationAssigned, and ThirdPartyAppAssigned.


```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Skip
Skips the first X returned results and the default value is 0.


```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TelephoneNumber
Filters the returned results to a specific phone number. It is optional to specify a prefixed "+". The phone number can not have "tel:" prefixed.
We support Direct Routing numbers with extensions using the formats +1206555000;ext=1234 or 1206555000;ext=1234.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TelephoneNumberContains
Filters the returned results based on substring match for the specified string on TelephoneNumber. For supported formats see TelephoneNumber.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TelephoneNumberGreaterThan
Filters the returned results based on greater than match for the specified string on TelephoneNumber. Can be used together with TelephoneNumberLessThan to specify a
range of phone numbers to return results for. For supported formats see TelephoneNumber.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TelephoneNumberLessThan
Filters the returned results based on less than match for the specified string on TelephoneNumber. Can be used together with TelephoneNumberGreaterThan to specify a
range of phone numbers to return results for. For supported formats see TelephoneNumber.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TelephoneNumberStartsWith
Filters the returned results based on starts with string match for the specified string on TelephoneNumber. For supported formats see TelephoneNumber.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Top
Returns the first X returned results and the default value is 500.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: 
Applicable: Microsoft Teams

Required: False
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### None

## OUTPUTS

### ActivationState
The activation state of the telephone number.

### AssignedPstnTargetId
The ID of the object the phone number is assigned to.

### Capability
The list of capabilities assigned to the phone number.

### CivicAddressId
The ID of the CivicAddress assigned to the phone number.


### IsoCountryCode
The ISO country code assigned to the phone number.

### LocationId
The ID of the Location assigned to the phone number.


### LocationUpdateSupported
Boolean stating if updating of the location assigned to the phone number is allowed.

### NumberType
The type of the phone number.

### PortInOrderStatus
The status of any port in order covering the phone number.

### PstnAssignmentStatus
The assignment status of the phone number.

### PstnPartnerId
The ID of the PSTN partner providing the phone number.

### PstnPartnerName
The name of the PSTN partner.

### TelephoneNumber
The phone number. The number is always displayed with prefixed "+", even if it was not assigned using prefixed "+".

The object returned is of type SkypeTelephoneNumberMgmtCmdletAcquiredTelephoneNumber.

## NOTES
The cmdlet is available in Teams PowerShell module 4.0.0 or later.

## RELATED LINKS
[Remove-CsPhoneNumberAssignment](Remove-CsPhoneNumberAssignment.md)

[Set-CsPhoneNumberAssignment](Set-CsPhoneNumberAssignment.md)

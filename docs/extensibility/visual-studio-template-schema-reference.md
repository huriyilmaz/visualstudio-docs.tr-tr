---
title: Visual Studio Şablon Şeması Başvurusu | Microsoft Docs
description: . Vstemplate dosyalarındaki XML öğelerini inceleyerek Visual Studio şablon şeması hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- VSTEMPLATE files
- Visual Studio templates, schema
- .vstemplate files
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9402efcc6c08343f1661945ae1701f7be7909bab
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903422"
---
# <a name="visual-studio-template-schema-reference"></a>Visual Studio Şablon Şeması Başvurusu
Bu bölüm, proje şablonları, öğe şablonları ve Başlangıç setleri için meta verileri depolayan dosyalar olan *. vstemplate* dosyalarındaki XML öğeleri hakkında bilgiler içerir.

 Özel *. vstemplate* dosyalarını doğrulamak için *vstemplate. xsd* ' de kullanabilirsiniz. Bu dosya, adresinde bulunabilir *. \\ \<Visual Studio installation folder> \Xml\Schemas\1033\vstemplate.xsd*.

|Öğe|Alt Öğeler|Öznitelikler|
|-------------|--------------------|----------------|
|[AppliesTo](../extensibility/appliesto-element-visual-studio-templates.md)|Yok|Yok|
|[Bütünleştirilmiş kod (şablon)](../extensibility/assembly-element-visual-studio-templates.md)|--|--|
|[Bütünleştirilmiş kod (sihirbaz uzantısı)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|--|--|
|[BuildProjectOnload](../extensibility/buildprojectonload-element-visual-studio-templates.md)|--|--|
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|--|--|
|[CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md)|--|--|
|[CustomDataSignature](../extensibility/customdatasignature-element-visual-studio-templates.md)|--|--|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|--|Ad<br /><br /> Değer|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|--|
|[DefaultName](../extensibility/defaultname-element-visual-studio-templates.md)|--|--|
|[Açıklama](../extensibility/description-element-visual-studio-templates.md)|--|Paket<br /><br /> ID|
|[EnableEditOfLocationField](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|--|--|
|[EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|--|--|
|[Klasör](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Klasör|Ad|
||[kullanım dışı]|--|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|--|--|
|[Gizli](../extensibility/hidden-element-visual-studio-templates.md)|--|--|
|[Simge](../extensibility/icon-element-visual-studio-templates.md)|--|Paket<br /><br /> ID|
|[LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md)|--|--|
|[LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|--|--|
|[MaxFrameworkVersion](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|--|--|
|[Ad](../extensibility/name-element-visual-studio-templates.md)|--|Paket<br /><br /> ID|
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|--|--|
|[PreviewImage](../extensibility/previewimage-element-visual-studio-templates.md)|--|--|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Klasör<br /><br /> ProjectItem|Dosya<br /><br /> TargetFileName<br /><br /> ReplaceParameters|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|--|
|[ProjectItem (öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)|--|SubType<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|
|[ProjectItem (proje şablonları)](../extensibility/projectitem-element-visual-studio-project-templates.md)|--|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|
|[ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)|--|--|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|--|ProjectName|
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|--|--|
|[PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|--|--|
|[ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md)|--|--|
|[Başvuru](../extensibility/reference-element-visual-studio-templates.md)|Bütünleştirilmiş Kod|--|
|[Başvurular](../extensibility/references-element-visual-studio-templates.md)|Başvuru|--|
|[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|--|--|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|--|Sürüm|
|[SDKReference](../extensibility/sdkreference-element-visual-studio-templates.md)|--|Paket|
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|--|--|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|Ad|
|[SortOrder](../extensibility/sortorder-element-visual-studio-templates.md)|--|--|
|[SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|--|--|
|[SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|--|--|
|[SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|--|--|
|[TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|--|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Project<br /><br /> Başvurular<br /><br /> ProjectItem<br /><br /> CustomParameters|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Ad<br /><br /> Açıklama<br /><br /> Simge<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Gizli<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|--|
|[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)|--|--|
|[TemplateID](../extensibility/templateid-element-visual-studio-templates.md)|--|--|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Tür<br /><br /> Sürüm|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|--|Ad|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Bütünleştirilmiş Kod<br /><br /> FullClassName|--|

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)

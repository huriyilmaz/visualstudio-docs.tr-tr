---
title: Seçenekler ve Seçenekler Sayfaları | Microsoft Docs
description: VSPackage'ın durumunu belirleyen seçeneklerin değerlerini değiştirmenizi sağlarken seçenekler sayfası desteği hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8e861539470579cc10f2dc41859237393b89fdf943b30ec0033cf2f033f862e6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359253"
---
# <a name="options-and-options-pages"></a>Seçenekler ve Seçenekler Sayfaları
Araçlar **menüsünde** **Seçenekler'e** tıklarken Seçenekler **iletişim** kutusu açılır. Bu iletişim kutusundaki seçenekler topluca seçenek sayfaları olarak adlandırılır. Gezinti bölmesindeki ağaç denetimi, seçenek kategorilerini içerir ve her kategorinin seçenek sayfaları vardır. Bir sayfayı seçerek sağ bölmede bu sayfayı seçebilirsiniz. Bu sayfalar VSPackage'ın durumunu belirleyen seçeneklerin değerlerini değiştirmenizi sağlar.

## <a name="support-for-options-pages"></a>Seçenekler Sayfaları desteği
 sınıfı, <xref:Microsoft.VisualStudio.Shell.Package> seçenek sayfaları ve seçenek kategorileri oluşturmak için destek sağlar. sınıfı <xref:Microsoft.VisualStudio.Shell.DialogPage> bir seçenekler sayfası uygulanır.

 varsayılan uygulaması, <xref:Microsoft.VisualStudio.Shell.DialogPage> genel özellikler kılavuzunda bir kullanıcıya genel özelliklerini sunar. Kendi kullanıcı arabirimine (UI) sahip özel seçenekler sayfası oluşturmak için sayfada çeşitli yöntemleri geçersiz karak bu davranışı özelleştirebilirsiniz. Daha fazla bilgi için [bkz. Seçenekler Sayfası Oluşturma.](../../extensibility/creating-an-options-page.md)

 sınıfı, <xref:Microsoft.VisualStudio.Shell.DialogPage> seçenek sayfaları ve kullanıcı ayarları için <xref:Microsoft.VisualStudio.Shell.IProfileManager> kalıcılık sağlayan 'i kullanır. Ve yöntemlerinin varsayılan uygulamaları, özelliğin bir dizeye ve dizeden dönüştürülmesi için kayıt defterinin kullanıcı bölümüne <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> yapılan özellik değişikliklerini kalıcı olarak bulundurmaktadır.

## <a name="options-page-registry-path"></a>Seçenekler Sayfası Kayıt Defteri Yolu
 Varsayılan olarak, seçenekler sayfası tarafından yönetilen özelliklerin kayıt defteri yolu , DialogPage sözcüğü ve seçenekler sayfa sınıfının tür adı <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> birleştirerek belirlenir. Örneğin, seçenekler sayfa sınıfı aşağıdaki gibi tanımlanabilir.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet1":::

 değeri <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, özellik adı ve değer çiftleri, HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral.

 Seçenekler sayfasının kayıt defteri yolu , toolsOptionsPages sözcüğü ve seçenekler sayfası kategorisi ile adı <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> birleştirerek belirlenir. Örneğin, Özel seçenekler sayfasında Seçenek Sayfalarım kategorisi varsa ve sayfası HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp ise seçenekler sayfasında kayıt defteri anahtarı <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Araçlar/Seçenekler Sayfası Öznitelikleri ve Düzeni
 özniteliği, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Seçenekler iletişim kutusunun gezinti ağacında özel seçenekler sayfalarının kategorilere **gruplamalarını** belirler. özniteliği, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> bir seçenekler sayfasını arabirimini sağlayan VSPackage ile ilişkilendirır. Aşağıdaki kod parçasını düşünün:

:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet2":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet2":::

 Bu, MyPackage'ın Iki seçenek sayfası sağladığını bildirer: OptionsPageGeneral ve OptionsPageCustom. Seçenekler **iletişim kutusunda** her iki seçenek  sayfası da Seçenek Sayfalarım kategorisinde sırasıyla **Genel** ve **Özel olarak** görünür.

## <a name="option-attributes-and-layout"></a>Seçenek Öznitelikleri ve Düzeni
 Sayfanın sağladığı kullanıcı arabirimi (UI), seçeneklerin özel seçenekler sayfasındaki görünümünü belirler. Genel seçenekler sayfasındaki seçeneklerin düzeni, etiketlemesi ve açıklaması aşağıdaki öznitelikler tarafından belirlenir:

- <xref:System.ComponentModel.CategoryAttribute> seçeneğin kategorisini belirler.

- <xref:System.ComponentModel.DisplayNameAttribute> seçeneğin görünen adını belirler.

- <xref:System.ComponentModel.DescriptionAttribute> seçeneğin açıklamasını belirler.

  > [!NOTE]
  > Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanır ve yönetilen [proje örneğinde tanımlanır.](/azure/devops/integrate/index)

  Aşağıdaki kod parçasını düşünün:

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs" id="Snippet3":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb" id="Snippet3":::

  Seçenekler sayfasında OptionInteger seçeneği, Seçeneklerim **kategorisinde Tamsayı** Seçeneği **olarak** görünür. Seçenek seçiliyse açıklama kutusunda Açıklama olan **Tamsayım** seçeneği görüntülenir.

## <a name="accessing-options-pages-from-another-vspackage"></a>Başka bir VSPackage'dan Seçenekler Sayfalarına Erişme
 Seçenekler sayfasını barındıran ve yöneten bir VSPackage'a otomasyon modeli kullanılarak program aracılığıyla başka bir VSPackage'dan erişilebilir. Örneğin, aşağıdaki kodda bir VSPackage seçenek sayfası barındırma olarak kaydedilir.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet4":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet4":::

 Aşağıdaki kod parçası, OptionInteger değerini MyOptionPage'den alır:

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet5":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet5":::

 Öznitelik bir seçenek sayfasını kaydettirirse, özniteliğin bağımsız değişkeni ise sayfa <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> AutomationProperties `SupportsAutomation` anahtarı altında `true` kaydedilir. Otomasyon, ilişkili VSPackage'ı bulmak için bu kayıt defteri girişini inceler ve otomasyon özelliğine barındırılan seçenekler sayfasından (bu durumda Kılavuzum Sayfası) erişer.

 Otomasyon özelliğinin kayıt defteri yolu , sözcüğü, AutomationProperties ve seçenekler sayfası kategorisi ile adı <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> birleştirerek belirlenir. Örneğin, seçenekler sayfasında Kategorim kategorisi, Kılavuzum Sayfası adı ve , HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp varsa otomasyon özelliği, Kategorim <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page.

> [!NOTE]
> Kurallı ad olan My Category.My Grid Page, bu anahtarın Name alt anahtarının değeridir.

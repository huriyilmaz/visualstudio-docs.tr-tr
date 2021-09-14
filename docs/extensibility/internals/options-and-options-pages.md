---
title: Seçenekler ve Seçenekler sayfası | Microsoft Docs
description: Bir VSPackage durumunu belirleyen seçeneklerin değerlerini değiştirmenize olanak sağlayan seçenek sayfaları için destek hakkında bilgi edinin.
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
ms.openlocfilehash: 6b83ef69d118f902d8c3d1acb1eff47384007a5c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725045"
---
# <a name="options-and-options-pages"></a>Seçenekler ve Seçenekler Sayfaları
**Araçlar** menüsünde **Seçenekler** ' i tıklatmak **Seçenekler** iletişim kutusunu açar. Bu iletişim kutusundaki seçenekler topluca seçenek sayfaları olarak adlandırılır. Gezinti bölmesindeki ağaç denetimi seçenek kategorilerini içerir ve her kategorinin seçenek sayfaları vardır. Bir sayfa seçtiğinizde, seçenekleri sağ bölmede görünür. Bu sayfalar, VSPackage 'un durumunu belirten seçeneklerin değerlerini değiştirmenize olanak sağlar.

## <a name="support-for-options-pages"></a>Seçenekler sayfaları için destek
 <xref:Microsoft.VisualStudio.Shell.Package>Sınıfı, seçenek sayfaları ve seçenek kategorileri oluşturmak için destek sağlar. <xref:Microsoft.VisualStudio.Shell.DialogPage>Sınıfı bir seçenekler sayfası uygular.

 Varsayılan uygulamasının genel özellikleri, bir <xref:Microsoft.VisualStudio.Shell.DialogPage> Genel Özellikler kılavuzunda bir kullanıcıya sunulur. Kendi kullanıcı arabirimi (UI) olan özel bir seçenekler sayfası oluşturmak için sayfadaki çeşitli yöntemleri geçersiz kılarak bu davranışı özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Seçenekler sayfası oluşturma](../../extensibility/creating-an-options-page.md).

 <xref:Microsoft.VisualStudio.Shell.DialogPage>Sınıfı <xref:Microsoft.VisualStudio.Shell.IProfileManager> , seçenek sayfaları ve ayrıca Kullanıcı ayarları için kalıcılık sağlayan öğesini uygular. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>Özelliği, ve <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> bir dizeye dönüştürülebileceğinden, ve yöntemlerinin varsayılan uygulamaları, kayıt defterinin bir Kullanıcı bölümünde değişir.

## <a name="options-page-registry-path"></a>Seçenekler sayfası kayıt defteri yolu
 Varsayılan olarak, bir seçenekler sayfası tarafından yönetilen özelliklerin kayıt defteri yolu <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> ,, Word DialogPage ve Seçenekler sayfası sınıfının tür adı birleştirilerek belirlenir. Örneğin, Seçenekler sayfası sınıfı aşağıdaki şekilde tanımlanabilir.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet1":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet1":::

 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> özellik adı ve değer çiftleri HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral alt anahtarlardır.

 Seçenekler sayfasının kayıt defteri yolu <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , sözcük, araçları seçenekleri sayfaları ve Seçenekler sayfası kategorisi ve adı birleştirilerek belirlenir. Örneğin, Özel Seçenekler sayfasında kategori, seçenek sayfaları ve <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp varsa, Seçenekler sayfası HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom kayıt defteri anahtarına sahiptir.

## <a name="toolsoptions-page-attributes-and-layout"></a>Araçlar/Seçenekler sayfası öznitelikleri ve düzeni
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Öznitelik, Özel Seçenekler sayfasının, **Seçenekler** iletişim kutusunun Gezinti ağacındaki Kategoriler ' e gruplandırılmasını belirler. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Özniteliği bir Seçenekler sayfasını arabirimini sağlayan VSPackage ile ilişkilendirir. Aşağıdaki kod parçasını göz önünde bulundurun:

:::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet2":::
:::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet2":::

 Bu, MyPackage 'ın iki seçenek sayfası sağladığını, Options Pagegeneral ve Optionspageczel olduğunu bildirir. **Seçenekler** iletişim kutusunda her iki seçenek sayfası sırasıyla **genel** ve **özel** olarak **seçenek sayfaları** kategorisinde görünür.

## <a name="option-attributes-and-layout"></a>Seçenek öznitelikleri ve düzeni
 Sayfanın sağladığı Kullanıcı arabirimi (UI), seçeneklerin görünümünü özel seçenekler sayfasında belirler. Genel Seçenekler sayfasındaki seçeneklerin düzeni, etiketlenmesi ve açıklaması aşağıdaki özniteliklere göre belirlenir:

- <xref:System.ComponentModel.CategoryAttribute> seçeneğin kategorisini belirler.

- <xref:System.ComponentModel.DisplayNameAttribute> seçeneğin görünen adını belirler.

- <xref:System.ComponentModel.DescriptionAttribute> seçeneğin açıklamasını belirler.

  > [!NOTE]
  > Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanır ve [yönetilen proje örneğinde](/azure/devops/integrate/index)tanımlanmıştır.

  Aşağıdaki kod parçasını göz önünde bulundurun:

  :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs" id="Snippet3":::
  :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb" id="Snippet3":::

  Seçenektamsayı seçeneği, Seçenekler sayfasında, **My Options** kategorisindeki **tamsayı seçeneği** olarak görünür. Seçenek işaretliyse, Açıklama kutusunda açıklama, **tamsayı seçeneği** görüntülenir.

## <a name="accessing-options-pages-from-another-vspackage"></a>Başka bir VSPackage 'tan seçenek sayfalarına erişme
 Seçenekler sayfasını barındıran ve yöneten bir VSPackage otomasyon modeli kullanılarak programlı bir şekilde başka bir VSPackage 'tan erişilebilir. Örneğin, aşağıdaki kodda bir VSPackage, bir seçenek sayfası barındırmak olarak kaydedilir.

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet4":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet4":::

 Aşağıdaki kod parçası, MyOptionPage öğesinden OptionInteger değerini alır:

 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs" id="Snippet5":::
 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb" id="Snippet5":::

 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Öznitelik bir seçenekler sayfası kaydettiğinde, `SupportsAutomation` öznitelik bağımsız değişkeni ise, sayfa AutomationProperties anahtarının altına kaydedilir `true` . Otomasyon, ilişkili VSPackage 'ı bulmak için bu kayıt defteri girişini inceler ve Otomasyon daha sonra barındırılan Seçenekler sayfası, bu durumda kılavuzum sayfam aracılığıyla özelliğe erişir.

 Automation özelliğinin kayıt defteri yolu <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , sözcük, AutomationProperties ve Seçenekler sayfası kategorisi ve adı birleştirilerek belirlenir. Örneğin, Seçenekler sayfasında kategorim kategorisi, My Grid Sayfamın adı ve <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp, ardından Automation özelliği, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page kayıt defteri anahtarına sahiptir.

> [!NOTE]
> Kurallı ad, My Category.My Grid sayfam, bu anahtarın Name alt anahtarının değeridir.

---
title: Seçenekler ve Seçenekler sayfası | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 963a73a3a8e079b2171c88e901913990892715cd
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981894"
---
# <a name="options-and-options-pages"></a>Seçenekler ve Seçenekler Sayfaları
**Araçlar** menüsünde **Seçenekler** ' i tıklatmak **Seçenekler** iletişim kutusunu açar. Bu iletişim kutusundaki seçenekler topluca seçenek sayfaları olarak adlandırılır. Gezinti bölmesindeki ağaç denetimi seçenek kategorilerini içerir ve her kategorinin seçenek sayfaları vardır. Bir sayfa seçtiğinizde, seçenekleri sağ bölmede görünür. Bu sayfalar, VSPackage 'un durumunu belirten seçeneklerin değerlerini değiştirmenize olanak sağlar.

## <a name="support-for-options-pages"></a>Seçenekler sayfaları için destek
 <xref:Microsoft.VisualStudio.Shell.Package> sınıfı, seçenek sayfaları ve seçenek kategorileri oluşturmak için destek sağlar. <xref:Microsoft.VisualStudio.Shell.DialogPage> sınıfı bir seçenekler sayfası uygular.

 <xref:Microsoft.VisualStudio.Shell.DialogPage> varsayılan uygulanması, genel özelliklerini bir dizi özelliğin genel kılavuzundaki bir kullanıcısına sunmaktadır. Kendi kullanıcı arabirimi (UI) olan özel bir seçenekler sayfası oluşturmak için sayfadaki çeşitli yöntemleri geçersiz kılarak bu davranışı özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Seçenekler sayfası oluşturma](../../extensibility/creating-an-options-page.md).

 <xref:Microsoft.VisualStudio.Shell.DialogPage> sınıfı, seçenek sayfaları ve ayrıca Kullanıcı ayarları için kalıcılık sağlayan <xref:Microsoft.VisualStudio.Shell.IProfileManager>uygular. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> ve <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> yöntemlerinin varsayılan uygulamaları, özelliği bir dizeye ve dizeden dönüştürülebileceğinden, özellik değişikliklerini kayıt defteri 'nin bir Kullanıcı bölümünde kalıcı olarak devam edebilir.

## <a name="options-page-registry-path"></a>Seçenekler sayfası kayıt defteri yolu
 Varsayılan olarak, bir seçenekler sayfası tarafından yönetilen özelliklerin kayıt defteri yolu, <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, Word DialogPage ve Seçenekler sayfası sınıfının tür adı birleştirilerek belirlenir. Örneğin, Seçenekler sayfası sınıfı aşağıdaki şekilde tanımlanabilir.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp ise, özellik adı ve değer çiftleri HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral. alt anahtarlardır

 Seçenekler sayfasının kayıt defteri yolu, <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, sözcük, araçları seçenekleri sayfaları ve Seçenekler sayfası kategorisi ve adı birleştirilerek belirlenir. Örneğin, Özel Seçenekler sayfasında kategori, seçenek sayfaları ve <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp ise, Seçenekler sayfasında kayıt defteri anahtarı bulunur, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\ 8.0 exp \ araçları seçeneklerim \ My OPTION Pages\Custom.

## <a name="toolsoptions-page-attributes-and-layout"></a>Araçlar/Seçenekler sayfası öznitelikleri ve düzeni
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> özniteliği, Özel Seçenekler sayfasının, **Seçenekler** iletişim kutusunun Gezinti ağacındaki kategorilere gruplandırılmasını belirler. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> özniteliği, bir seçenek sayfasını arabirimini sağlayan VSPackage ile ilişkilendirir. Aşağıdaki kod parçasını göz önünde bulundurun:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Bu, MyPackage 'ın iki seçenek sayfası sağladığını, Options Pagegeneral ve Optionspageczel olduğunu bildirir. **Seçenekler** iletişim kutusunda her iki seçenek sayfası sırasıyla **genel** ve **özel**olarak **seçenek sayfaları** kategorisinde görünür.

## <a name="option-attributes-and-layout"></a>Seçenek öznitelikleri ve düzeni
 Sayfanın sağladığı Kullanıcı arabirimi (UI), seçeneklerin görünümünü özel seçenekler sayfasında belirler. Genel Seçenekler sayfasındaki seçeneklerin düzeni, etiketlenmesi ve açıklaması aşağıdaki özniteliklere göre belirlenir:

- <xref:System.ComponentModel.CategoryAttribute>, seçeneğin kategorisini belirler.

- <xref:System.ComponentModel.DisplayNameAttribute>, seçeneğin görünen adını belirler.

- <xref:System.ComponentModel.DescriptionAttribute>, seçeneğinin açıklamasını belirler.

  > [!NOTE]
  > Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanır ve [yönetilen proje örneğinde](/azure/devops/integrate/index)tanımlanmıştır.

  Aşağıdaki kod parçasını göz önünde bulundurun:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  Seçenektamsayı seçeneği, Seçenekler sayfasında, **My Options** kategorisindeki **tamsayı seçeneği** olarak görünür. Seçenek işaretliyse, Açıklama kutusunda açıklama, **tamsayı seçeneği**görüntülenir.

## <a name="accessing-options-pages-from-another-vspackage"></a>Başka bir VSPackage 'tan seçenek sayfalarına erişme
 Seçenekler sayfasını barındıran ve yöneten bir VSPackage otomasyon modeli kullanılarak programlı bir şekilde başka bir VSPackage 'tan erişilebilir. Örneğin, aşağıdaki kodda bir VSPackage, bir seçenek sayfası barındırmak olarak kaydedilir.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Aşağıdaki kod parçası, MyOptionPage öğesinden OptionInteger değerini alır:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> özniteliği bir Seçenekler sayfasını kaydettiğinde, özniteliğin `SupportsAutomation` bağımsız değişkeni `true`ise, sayfa AutomationProperties anahtarının altına kaydedilir. Otomasyon, ilişkili VSPackage 'ı bulmak için bu kayıt defteri girişini inceler ve Otomasyon daha sonra barındırılan Seçenekler sayfası, bu durumda kılavuzum sayfam aracılığıyla özelliğe erişir.

 Automation özelliğinin kayıt defteri yolu <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, sözcük, AutomationProperties ve Seçenekler sayfası kategorisi ve adı birleştirilerek belirlenir. Örneğin, Seçenekler sayfasında kategorim kategorisi, My Grid Sayfamın adı ve <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp ve ardından Automation özelliği kayıt defteri anahtarına sahiptir, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ VisualStudio\8.0Exp\AutomationProperties\My Category\grid sayfası.

> [!NOTE]
> Kurallı ad, My Category.My Grid sayfam, bu anahtarın Name alt anahtarının değeridir.
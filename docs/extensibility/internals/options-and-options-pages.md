---
title: Seçenekler ve Seçenekler Sayfaları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706836"
---
# <a name="options-and-options-pages"></a>Seçenekler ve Seçenekler Sayfaları
**Araçlar** menüsünde **Seçenekler'i** tıklatarak **Seçenekler** iletişim kutusunu açar. Bu iletişim kutusundaki seçenekler topluca seçenek sayfaları olarak adlandırılır. Gezinti bölmesindeki ağaç denetimi seçenekler kategorilerini içerir ve her kategoride seçenekler sayfaları vardır. Bir sayfa seçtiğinizde, sayfaseçenekleri sağ bölmede görünür. Bu sayfalar, vspackage durumunu belirleyen seçeneklerin değerlerini değiştirmenize izin verir.

## <a name="support-for-options-pages"></a>Seçenekler Sayfaları için Destek
 Sınıf, <xref:Microsoft.VisualStudio.Shell.Package> seçenekler sayfaları ve seçenekler kategorileri oluşturmak için destek sağlar. Sınıf <xref:Microsoft.VisualStudio.Shell.DialogPage> bir seçenekler sayfası uygular.

 Genel bir <xref:Microsoft.VisualStudio.Shell.DialogPage> özellik tablosunda ortak özelliklerini kullanıcıya sunan varsayılan uygulama. Kendi kullanıcı arabirimi (UI) olan özel bir seçenek sayfası oluşturmak için sayfadaki çeşitli yöntemleri geçersiz kılarak bu davranışı özelleştirebilirsiniz. Daha fazla bilgi için seçenekler [sayfası oluşturma](../../extensibility/creating-an-options-page.md)sayfasına bakın.

 <xref:Microsoft.VisualStudio.Shell.IProfileManager>Sınıf, <xref:Microsoft.VisualStudio.Shell.DialogPage> seçenekler sayfaları ve kullanıcı ayarları için kalıcılık sağlayan uygular. Özellik bir dize <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> dönüştürülebilir ve bu özellik kayıt defterinin bir kullanıcı bölümüne mülkiyet değişiklikleri devam ve yöntemlerin varsayılan uygulamaları.

## <a name="options-page-registry-path"></a>Seçenekler Sayfa Kayıt Yolu
 Varsayılan olarak, seçenekler sayfası tarafından yönetilen özelliklerin kayıt defteri <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>yolu, Sözcük Iletişim Sayfası ve seçenekler sayfası sınıfının tür adı birleştirilerek belirlenir. Örneğin, seçenekler sayfası sınıfı aşağıdaki gibi tanımlanabilir.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> ise, özellik adı ve değer çiftleri HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral alt anahtarlarıdır.

 Seçenekler sayfasının kayıt defteri yolu, sözcük, ToolsOptionsPages ve seçenekler sayfası kategorisi ve adı birleştirilerek <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>belirlenir. Örneğin, Özel seçenekler sayfasında Seçenek Sayfalarım kategorisi varsa <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> ve HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp ise, seçenekler sayfasında kayıt defteri anahtarı HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsOptionsPages\My Option Pages\Custom vardır.

## <a name="toolsoptions-page-attributes-and-layout"></a>Araçlar/Seçenekler Sayfa Öznitelikleri ve Düzeni
 Öznitelik, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> özel seçenekler sayfalarının **Seçenekler** iletişim kutusunun gezinti ağacındaki kategorilerhalinde gruplandırmasını belirler. Öznitelik, <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> arabirimi sağlayan VSPackage ile bir seçenek sayfasını ilişkilendirer. Aşağıdaki kod parçasını göz önünde bulundurun:

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 Bu, MyPackage'ın OptionsPageGeneral ve OptionsPageCustom olmak üzere iki seçenek sayfası sağladığını bildirir. **Seçenekler** iletişim kutusunda, her iki seçenek sayfası da **Seçenek Sayfaları Miçin** **Genel** ve **Özel**olarak görünür.

## <a name="option-attributes-and-layout"></a>Seçenek Öznitelikleri ve Düzeni
 Sayfanın sağladığı kullanıcı arabirimi (UI), özel seçenekler sayfasındaki seçeneklerin görünümünü belirler. Genel seçenekler sayfasındaki seçeneklerin düzeni, etiketi ve açıklaması aşağıdaki özniteliklere göre belirlenir:

- <xref:System.ComponentModel.CategoryAttribute>seçeneğin kategorisini belirler.

- <xref:System.ComponentModel.DisplayNameAttribute>seçeneğin görüntü adını belirler.

- <xref:System.ComponentModel.DescriptionAttribute>seçeneğin açıklamasını belirler.

  > [!NOTE]
  > Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanır ve [yönetilen proje örneğinde](/azure/devops/integrate/index)tanımlanır.

  Aşağıdaki kod parçasını göz önünde bulundurun:

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  OptionInteger seçeneği seçenekler sayfasında **Seçeneklerim** kategorisinde **Integer Seçeneği** olarak görünür. Seçenek seçilirse, açıklama, **tamsayı seçeneği,** açıklama kutusunda görüntülenir.

## <a name="accessing-options-pages-from-another-vspackage"></a>Başka bir VSPackage'dan Seçenekler Sayfalarına Erişim
 Seçenekler sayfasını barındıran ve yöneten bir VSPackage'a otomasyon modeli kullanılarak başka bir VSPackage'dan programlanabilir. Örneğin, aşağıdaki kodda bir VSPackage bir seçenek sayfası barındırma olarak kaydedilir.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 Aşağıdaki kod parçası MyOptionPage OptionInteger değerini alır:

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> Öznitelik bir seçenek sayfasını kaydettiğinde, öznitelik `SupportsAutomation` bağımsız değişkeni `true`. Otomasyon ilişkili VSPackage bulmak için bu kayıt defteri girişini inceler ve otomasyon sonra barındırılan seçenekler sayfası üzerinden özellik erişir, Bu durumda, Benim Grid Sayfası.

 Otomasyon özelliğinin kayıt yolu, sözcük, <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>AutomationProperties ve seçenekler sayfası kategorisi ve adı birleştirilerek belirlenir. Örneğin, seçenekler sayfasında Kategorim kategorisi, Izgara Sayfam adı <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>ve , HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp varsa, otomasyon özelliğinde kayıt defteri anahtarı HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My Grid Page vardır.

> [!NOTE]
> Kanonik adı, Benim Category.My Izgara Sayfası, bu anahtarın Ad alt anahtarının değeridir.

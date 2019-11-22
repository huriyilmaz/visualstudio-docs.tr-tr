---
title: Seçenekler ve Seçenekler sayfası | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e30be26c40834d3122d491f8d150f02b6f3b776
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300693"
---
# <a name="options-and-options-pages"></a>Seçenekler ve Seçenekler Sayfaları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Araçlar** menüsünde **Seçenekler** ' i tıklatmak **Seçenekler** iletişim kutusunu açar. Bu iletişim kutusundaki seçenekler topluca seçenek sayfaları olarak adlandırılır. Gezinti bölmesindeki ağaç denetimi seçenek kategorilerini içerir ve her kategorinin seçenek sayfaları vardır. Bir sayfa seçtiğinizde, seçenekleri sağ bölmede görünür. Bu sayfalar, VSPackage 'un durumunu belirten seçeneklerin değerlerini değiştirmenize olanak sağlar.  
  
## <a name="support-for-options-pages"></a>Seçenekler sayfaları için destek  
 <xref:Microsoft.VisualStudio.Shell.Package> sınıfı, seçenek sayfaları ve seçenek kategorileri oluşturmak için destek sağlar. <xref:Microsoft.VisualStudio.Shell.DialogPage> sınıfı bir seçenekler sayfası uygular.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> varsayılan uygulanması, genel özelliklerini bir dizi özelliğin genel kılavuzundaki bir kullanıcısına sunmaktadır. Kendi kullanıcı arabirimi (UI) olan özel bir seçenekler sayfası oluşturmak için sayfadaki çeşitli yöntemleri geçersiz kılarak bu davranışı özelleştirebilirsiniz. Daha fazla bilgi için bkz. [Seçenekler sayfası oluşturma](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> sınıfı, seçenek sayfaları ve ayrıca Kullanıcı ayarları için kalıcılık sağlayan <xref:Microsoft.VisualStudio.Shell.IProfileManager>uygular. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> ve <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> yöntemlerinin varsayılan uygulamaları, özelliği bir dizeye ve dizeden dönüştürülebileceğinden, özellik değişikliklerini kayıt defteri 'nin bir Kullanıcı bölümünde kalıcı olarak devam edebilir.  
  
## <a name="options-page-registry-path"></a>Seçenekler sayfası kayıt defteri yolu  
 Varsayılan olarak, bir seçenekler sayfası tarafından yönetilen özelliklerin kayıt defteri yolu, <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, Word DialogPage ve Seçenekler sayfası sınıfının tür adı birleştirilerek belirlenir. Örneğin, Seçenekler sayfası sınıfı aşağıdaki şekilde tanımlanabilir.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, \Software\Microsoft\VisualStudio\8.0Exp HKEY_CURRENT_USER, özellik adı ve değer çiftleri HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPageGeneral. alt anahtarlardır  
  
 Seçenekler sayfasının kayıt defteri yolu, <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, sözcük, araçları seçenekleri sayfaları ve Seçenekler sayfası kategorisi ve adı birleştirilerek belirlenir. Örneğin, Özel Seçenekler sayfasında kategori, seçenek sayfaları ve <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp ise, Seçenekler sayfasında kayıt defteri anahtarı HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio\8.0exp\tools\optionspages\option Pages\Custom.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Araçlar/Seçenekler sayfası öznitelikleri ve düzeni  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> özniteliği, Özel Seçenekler sayfasının, **Seçenekler** iletişim kutusunun Gezinti ağacındaki kategorilere gruplandırılmasını belirler. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> özniteliği, bir seçenek sayfasını arabirimini sağlayan VSPackage ile ilişkilendirir. Aşağıdaki kod parçasını göz önünde bulundurun:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Bu, MyPackage 'ın iki seçenek sayfası sağladığını, Options Pagegeneral ve Optionspageczel olduğunu bildirir. **Seçenekler** iletişim kutusunda her iki seçenek sayfası sırasıyla **genel** ve **özel**olarak **seçenek sayfaları** kategorisinde görünür.  
  
## <a name="option-attributes-and-layout"></a>Seçenek öznitelikleri ve düzeni  
 Sayfanın sağladığı Kullanıcı arabirimi (UI), seçeneklerin görünümünü özel seçenekler sayfasında belirler. Genel Seçenekler sayfasındaki seçeneklerin düzeni, etiketlenmesi ve açıklaması aşağıdaki özniteliklere göre belirlenir:  
  
- <xref:System.ComponentModel.CategoryAttribute>, seçeneğin kategorisini belirler.  
  
- <xref:System.ComponentModel.DisplayNameAttribute>, seçeneğin görünen adını belirler.  
  
- <xref:System.ComponentModel.DescriptionAttribute>, seçeneğinin açıklamasını belirler.  
  
  > [!NOTE]
  > Eşdeğer öznitelikler, SRCategory, LocDisplayName ve SRDescription, yerelleştirme için dize kaynaklarını kullanır ve [yönetilen proje örneğinde](https://go.microsoft.com/fwlink/?LinkId=122774)tanımlanmıştır.  
  
  Aşağıdaki kod parçasını göz önünde bulundurun:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  Seçenektamsayı seçeneği, Seçenekler sayfasında, **My Options** kategorisindeki **tamsayı seçeneği** olarak görünür. Seçenek işaretliyse, Açıklama kutusunda açıklama, **tamsayı seçeneği**görüntülenir.  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Başka bir VSPackage 'tan seçenek sayfalarına erişme  
 Seçenekler sayfasını barındıran ve yöneten bir VSPackage otomasyon modeli kullanılarak programlı bir şekilde başka bir VSPackage 'tan erişilebilir. Örneğin, aşağıdaki kodda bir VSPackage, bir seçenek sayfası barındırmak olarak kaydedilir.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Aşağıdaki kod parçası, MyOptionPage öğesinden OptionInteger değerini alır:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> özniteliği bir Seçenekler sayfasını kaydettiğinde, özniteliğin `SupportsAutomation` bağımsız değişkeni `true`ise, sayfa AutomationProperties anahtarının altına kaydedilir. Otomasyon, ilişkili VSPackage 'ı bulmak için bu kayıt defteri girişini inceler ve Otomasyon daha sonra barındırılan Seçenekler sayfası, bu durumda kılavuzum sayfam aracılığıyla özelliğe erişir.  
  
 Automation özelliğinin kayıt defteri yolu <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, sözcük, AutomationProperties ve Seçenekler sayfası kategorisi ve adı birleştirilerek belirlenir. Örneğin, Seçenekler sayfasında kategorim kategorisi, kılavuz sayfam adı ve <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp varsa Automation özelliğinin kayıt defteri anahtarı HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\grid sayfası vardır.  
  
> [!NOTE]
> Kurallı ad, My Category.My Grid sayfam, bu anahtarın Name alt anahtarının değeridir.

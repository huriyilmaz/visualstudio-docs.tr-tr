---
title: SharePoint çözümlerini yerelleştirme | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6444f559902841c13a56265569a0bdc13a9ed26
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981731"
---
# <a name="localize-sharepoint-solutions"></a>SharePoint çözümlerini yerelleştirin

  Uygulamalarınızı, dünya çapındaki kullanılabilir olmaları için hazırlama işlemi, yerelleştirme olarak bilinir. Yerelleştirme, kaynakları belirli bir kültüre çevirdir. Daha fazla bilgi için bkz. [uygulamaları Genelleştirme ve yerelleştirme](../ide/globalizing-and-localizing-applications.md). Bu konuda bir SharePoint çözümünü yerelleştirmek için bir genel bakış sunulmaktadır.

 Bir çözümü yerelleştirmek için, koddan sabit kodlanmış dizeleri kaldırır ve bunları kaynak dosyalara soyutlar. Kaynak dosyası, *. resx* uzantılı [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]tabanlı bir dosyadır. Kaynak dosyası, çözümünüzde kullanılan dizelerin çevrilmiş sürümlerini içerir. Daha fazla bilgi için bkz. [uygulamalardaki kaynaklar](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100)).

> [!NOTE]
> SharePoint çözüm kaynak dosyalarına yalnızca dize kaynakları ekleyin. Kaynak Düzenleyicisi dize olmayan kaynaklar eklemenize izin verse de, dize olmayan kaynaklar SharePoint 'e dağıtılmaz.

## <a name="resource-files"></a>Kaynak dosyalar
 Üç tür kaynak dosyası vardır: varsayılan, dilden bağımsız ve dile özgü.

|Kaynak dosya türü|Açıklama|
|------------------------|-----------------|
|Varsayılan|Geri dönüş kaynağı olarak da bilinen varsayılan kaynak dosyaları, Ingilizce gibi varsayılan kültür için yerelleştirilmiş dizeler içerir. Belirtilen dil için yerelleştirilmiş kaynak dosyası bulunamazsa bunlar kullanılır. Varsayılan kaynakların ayrı dosyaları yoktur, bunlar ana uygulama derlemesinde depolanır.|
|Dilden bağımsız|Bir dil için yerelleştirilmiş dizeleri içeren, ancak belirli bir kültür olmayan bir kaynak dosyası. Örneğin, Fransızca için "fr".|
|Dile özgü|Bir dil ve kültür için yerelleştirilmiş dizeler içeren bir kaynak dosyası. Örneğin, Kanada Fransızcası için "fr-CA".|

 Daha fazla bilgi için bkz. [Yerelleştirme Için kaynakların hiyerarşik organizasyonu](../ide/hierarchical-organization-of-resources-for-localization.md).

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]yönettiğiniz SharePoint projelerinde varsayılan kaynak dosyalarını belirtmek için, bir kaynak dosyası eklerken **Kaynak Ekle** iletişim kutusunun kültür listesinden **sabit dil (Sabit ülke)** öğesini seçin.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Visual Studio SharePoint çözümlerini yerelleştirme
 Bir çözümü Yerelleştirebileceğiniz zaman, çözümünüzün kullanıcılara gösterdiği tüm metin bilgilerini dikkate almalısınız. Bilgi iletileri, hata iletileri ve [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] dizeleri çevrilmeli ve bu çeviriler kaynak dosyalarına yerleştirilmelidir.

 Bir kaynak dosyasındaki her dize benzersiz bir tanımlayıcıya sahiptir. Her kaynak dosyasındaki çevrilmiş dize için aynı tanımlayıcıyı kullanın. Örneğin, "Dize1" varsayılan kaynak dosyasındaki ilk dizenin tanıtıcısıdır, dile özgü kaynak dosyalarındaki ilk dize için aynı tanımlayıcıyı kullanın.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint uygulamalarında genellikle Yerelleştirebileceğiniz üç alan vardır: özellikler, ASPX sayfa biçimlendirme ve kod. İllüstrasyon amaçları doğrultusunda aşağıdaki bölümlerde, Almanca ve Japonca 'ya yerelleştirmek istediğiniz bir SharePoint çözümünün olduğunu varsayalım. Varsayılan dil Ingilizce 'dir.

### <a name="localize-features"></a>Özellikleri yerelleştirin
 Bir özelliği yerelleştirmek için, özelliğin sabit kodlanmış başlığını ve açıklamasını yerelleştirilmiş kaynaklar dosyasındaki çevrilmiş başlığa ve dizeye başvuran bir ifadeyle değiştirmeniz gerekir. Bu değişikliği [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]**özellik tasarımcısında** yaparsınız. Daha fazla bilgi için bkz. [nasıl yapılır: bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md).

 Ingilizce özelliğini Almanca ve Japonca olarak yerelleştirmek için projenize üç kaynak dosyası proje öğesi eklersiniz: biri Ingilizce, biri Almanca ve Japonca için bir tane. Özellik kaynak dosyaları ASPX işaretlemesini veya kodunu yerelleştirmek için kullanılamaz; Bunlar için ayrı kaynak dosyaları gereklidir.

 Özellik kaynak dosyalarını oluşturduktan sonra, bunlara çevrilmiş dizeler ekleyin. Yerelleştirilmiş dizelere aşağıdaki biçimde bir ifadeyle erişin:

```aspx-csharp
$Resources:String ID
```

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Özellik kaynakları her zaman kaynaklar olarak adlandırılır. Sabit dil dışında bir dil seçerseniz, kaynak dosyası adına bir kültür [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] eklenir. Örneğin, bir sabit dil (varsayılan) özellik kaynak dosyası eklerseniz, *Resources. resx*olarak adlandırılır. Japonca (Japonya) kültürü seçerek dile özgü bir özellik kaynağı eklerseniz, dosya *Resources. ja-JP. resx*olarak adlandırılır. Özellik kaynak dosyası adları otomatik olarak atanır ve değiştirilemez.

 Özellik Kaynaklarının kapsamı, eklendiği özellik için yereldir. Çözümde herhangi bir özellik veya öğe dosyası tarafından kullanılabilecek kaynaklar oluşturmak için, bir özellik kaynak dosyası yerine bir **genel kaynak dosyası** proje öğesi ekleyin. **Genel kaynak dosyası** proje öğesi, **Yeni öğe Ekle** iletişim kutusunda **SharePoint** altındaki **2010** klasöründe bulunur. Genel kaynak dosyaları, SharePoint kök klasörünün \Resources klasörüne dağıtılır.

### <a name="localize-aspx-page-markup"></a>ASPX sayfası işaretlemesini yerelleştirin
 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sayfaları yerelleştirmek için projenize üç kaynak dosyası proje öğesi eklersiniz: biri Ingilizce, biri Almanca ve Japonca için bir tane. Biçimlendirmeye ek olarak kodu yerelleştirmeniz gerekmez, bunun yerine genel kaynak dosyaları da ekleyebilirsiniz.

 Varsayılan dil kaynak dosyası için bir ad girin. Yerelleştirilmiş kaynak dosyalarına dile özgü kültür [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]eklenmiş aynı adı verin. Örneğin, Almanca ve MyAppResources için *MyAppResources.de-de. resx* , Japonca için. *ja-JP. resx* .

 Her kaynak dosyasının **dağıtım türü** özelliğini **AppGlobalResource**olarak ayarlayın. Bu, kaynak dosyalarının Çözümdeki tüm ASPX sayfaları ve denetimleri tarafından kullanılabildiği App_GlobalResources klasörüne dağıtılmasını sağlar. App_GlobalResources klasörü C:\inetpub\wwwroot\wss\virtualdizinlerinde\\< bağlantı noktası numarası\>\App_globalresourcesdizininde bulunur.

> [!NOTE]
> Genel olmayan kaynak dosyaları kullanırsanız, dağıtım türü özelliğini ve SharePoint 'e özgü diğer özellikleri etkinleştirmek için bunları proje öğesi klasörüne taşıyın.

 ASPX işaretleme kaynak dosyaları, kodu yerelleştirmek için de kullanılabilir. ASPX işaretlemesinin yanı sıra kodu yerelleştirmek için kaynaklar kullanıyorsanız, kaynağın bir uydu derlemesine derlenmesine neden olmak için her bir dosyanın derleme eylemi özelliği ayarını gömülü kaynak olarak bırakın. Ancak, kaynak dosyalarını yalnızca biçimlendirmeyi yerelleştirmek için kullanıyorsanız, dosyanın ana uygulama derlemesine derlenmesi için isteğe bağlı olarak yapı eylemini Içeriğe dönüştürebilirsiniz.

 ASPX sayfalarınızdaki tüm sabit kodlanmış Özellik dizelerini değiştirin ve biçimlendirmeyi aşağıdaki biçimde bir ifadeyle kontrol edin:

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Örneğin:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 ASPX için metin olarak aşağıdaki biçimde bir ifade kullanın:

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 Örneğin:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 Daha fazla bilgi için bkz. [nasıl yapılır:, aspx Işaretlemesini yerelleştirme](../sharepoint/how-to-localize-aspx-markup.md).

### <a name="localize-code"></a>Kodu yerelleştirin
 Özellik dizelerini ve [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] biçimlendirmeyi yerelleştirmenin yanı sıra, çözüm kodunuzda görüntülenen ileti dizelerini ve hata dizelerini de yerelleştirmeniz gerekir. Yerelleştirilmiş bilgilendirme ve hata iletileri uydu Derlemeleriyle bulunur. Uydu derlemeleri, kullanıcılar için görünür olan ve özel durumlar gibi [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] metin ve çıkış iletileri gibi dizeleri içerir.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] standart .NET Framework hub ve bağlı bileşen modelini kullanır. Hub veya ana program derlemesi, varsayılan dil kaynaklarını içerir. Bağlı bileşenler veya uydu derlemeleri dile özgü kaynakları içerir. Daha fazla bilgi için bkz. [kaynakları paketleme ve dağıtma](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100)). Uydu derlemeleri kaynak ( *. resx*) dosyalarından derlenir. Projenize ve çözüm paketine dile özgü kaynak dosyaları eklediğinizde, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kaynak dosyalarını *{Project Name}. resources. dll*adlı uydu Derlemeleriyle derler.

 ASPX biçimlendirmesinde olduğu gibi, projenize ayrı kaynak dosyası proje öğeleri ekleyerek SharePoint uygulama kodunu yerelleştirin; biri varsayılan dil ve diğeri her yerelleştirilmiş dil için. Ancak, daha önce belirtildiği gibi, ASPX işaretlemesini yerelleştirme için kaynak dosyalarınız zaten varsa, kodu yerelleştirme için yeniden kullanabilirsiniz. Kaynak dosyaları oluşturmanız gerekiyorsa, varsayılan dil kaynak dosyasına bir *. resx* uzantısıyla tercih ettiğiniz bir ad verin. Yerelleştirilmiş kaynak dosyalarını dile özgü kültüre [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]adı eklenmiş şekilde adlandırın. Uydu kaynak derlemelerinin oluşturulmasını sağlamak için her kaynak dosyanın derleme eylemi özelliğini gömülü kaynak olarak ayarlayın.

 Uydu derlemelerini oluşturmak için, projeyi derleyin ve sonra **paket tasarımcısının** **Gelişmiş** sekmesinde dosyaları ek derlemeler olarak ekleyin. Derlemeleri eklerken, konum yoluna bir kültür [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] klasörü ekleyin; örneğin, *\\{proje öğesi adı}. resources. dll*. Bu, paketin aynı ada sahip dosyalar içermesini sağlar.

 Kodunuzda, sabit kodlanmış dizeleri aşağıdaki sözdizimini kullanarak <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metoduna yapılan çağrılarla değiştirin:

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 Daha fazla bilgi için bkz. [nasıl yapılır: kod yerelleştirin](../sharepoint/how-to-localize-code.md).

#### <a name="web-part-code-localization"></a>Web bölümü kod yerelleştirme
 Web bölümleri, WebDisplayName, Category ve WebDescription gibi sabit kodlanmış dizeler kullanan kod öznitelikleri içeren özel bir özellik Düzenleyici özelliği içerir. Bu özniteliklerin dize değerlerini değiştirmek için, özniteliğin sınıfından türeyen ayrı bir sınıf oluşturun. Bu sınıflarda özniteliğin özelliğini ayarlayın. Öznitelik özelliği temel sınıfa bağlıdır. Örneğin, WebDisplayName özniteliği özelliği DisplayNameValue ve WebDescription öznitelik özelliği DescriptionValue ' dır.

 Türetilmiş sınıfta, dize KIMLIĞI için yerelleştirilmiş değeri almak üzere kaynak dosyasındaki dize KIMLIĞINE ve ResourceManager nesnesine başvurun. Bu değeri Özellik Düzenleyicisi özniteliğine döndürün.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md)
- [Nasıl yapılır: ASPX işaretlemesini yerelleştirme](../sharepoint/how-to-localize-aspx-markup.md)
- [Nasıl yapılır: kod yerelleştirme](../sharepoint/how-to-localize-code.md)
- [Nasıl yapılır: kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)
- [Nasıl yapılır: yerelleştirilmiş adları, özellikleri ve izinleri belirtmek için kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)

---
title: 'İzlenecek yol: eski dil hizmeti oluşturma | Microsoft Docs'
description: Visual C# ' de bir dil hizmeti uygulamak için yönetilen paket çerçevesi dil sınıflarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a0f3e497368047cec2ce1518e7b01f59a8895fbc
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724987"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>İzlenecek yol: Eski Dil Hizmeti oluşturma
' De bir dil hizmetini uygulamak için yönetilen paket çerçevesi (MPF) dil sınıflarının kullanılması [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] basittir. Dil hizmetini, dil hizmetini ve diliniz için bir ayrıştırıcısı barındırmak üzere bir VSPackage gerekir.

## <a name="prerequisites"></a>Önkoşullar
 bu yönergeyi izlemek için Visual Studio SDK 'sını yüklemelisiniz. daha fazla bilgi için bkz. [SDK Visual Studio](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio paketi Project şablonu konumları
 Visual Studio paketi Project şablonu, **yeni Project** iletişim kutusunda üç farklı şablon konumu içinde bulunabilir:

1. Visual Basic genişletilebilirlik altında. Projenin varsayılan dili Visual Basic.

2. C# genişletilebilirliği altında. Projenin varsayılan dili C# ' dir.

3. diğer Project türleri altında genişletilebilirlik. Projenin varsayılan dili C++ ' dır.

### <a name="create-a-vspackage"></a>VSPackage oluşturma

1. Visual Studio paketi proje şablonuyla yeni bir vspackage oluşturun.

    Var olan bir VSPackage 'a dil hizmeti ekliyorsanız, aşağıdaki adımları atlayın ve doğrudan "dil hizmeti sınıfı oluşturma" yordamına gidin.

2. Projenin adı için MyLanguagePackage girin ve **Tamam**' a tıklayın.

    Dilediğiniz adı kullanabilirsiniz. Burada ayrıntılı olarak, ad olarak MyLanguagePackage varsayılır.

3. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]Dil olarak seçin ve yeni bir anahtar dosyası oluşturma seçeneğini belirleyin. **İleri**’ye tıklayın.

4. Uygun şirket ve paket bilgilerini girin. **İleri**’ye tıklayın.

5. **Menü komutunu** seçin. **İleri**’ye tıklayın.

    Kod parçacıklarını desteklemeyi düşünmüyorsanız, yalnızca son ' a tıklayabilir ve sonraki adımı yoksayabilirsiniz.

6. Komut **adı** ve komut kimliği olarak **ekleme kod parçacığını** girin `cmdidInsertSnippet` . **Finish (Son)** düğmesine tıklayın.

    **Komut adı** ve **komut kimliği** istediğiniz şey olabilir. bunlar yalnızca örnektir.

### <a name="create-the-language-service-class"></a>Dil hizmeti sınıfını oluşturma

1. **Çözüm Gezgini**, MyLanguagePackage projesine sağ tıklayın, **Ekle**, **başvuru** ve ardından **Yeni Başvuru Ekle** düğmesini seçin.

2. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesinde **Microsoft. VisualStudio. Package. LanguageService** ' i seçin ve **Tamam**' ı tıklatın.

     Bu, dil paketi projesi için yalnızca bir kez yapılmalıdır.

3. **Çözüm Gezgini**' de, VSPackage projesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin.

4. Şablon listesinde **sınıfın** seçildiğinden emin olun.

5. Sınıf dosyasının adı için **MyLanguageService. cs** girin ve **Ekle**' ye tıklayın.

     Dilediğiniz adı kullanabilirsiniz. Burada ayrıntılı `MyLanguageService` olarak açıklanan yordamlar adı olarak varsayılır.

6. MyLanguageService. cs dosyasında aşağıdaki `using` yönergeleri ekleyin.

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs" id="Snippet1":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb" id="Snippet1":::

7. Sınıfından `MyLanguageService` türetmek için sınıfı değiştirin <xref:Microsoft.VisualStudio.Package.LanguageService> :

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs" id="Snippet2":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb" id="Snippet2":::

8. İmleci "LanguageService" üzerine konumlandırın ve **Düzenle**, **IntelliSense** menüsünde, **soyut sınıf Uygula**' yı seçin. Bu, dil hizmeti sınıfını uygulamak için gereken en düşük yöntemleri ekler.

9. [Eski dil hizmetini uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)bölümünde açıklandığı gibi soyut yöntemleri uygulayın.

### <a name="register-the-language-service"></a>Dil hizmetini kaydetme

1. MyLanguagePackagePackage. cs dosyasını açın ve aşağıdaki `using` yönergeleri ekleyin:

     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb" id="Snippet3":::
     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs" id="Snippet3":::

2. Dil hizmeti sınıfınızı, [eski dil hizmetini kaydettirme](../../extensibility/internals/registering-a-legacy-language-service1.md)konusunda açıklandığı gibi kaydettirin. Bu, ProvideXX özniteliklerini ve "dil hizmetini güçlendirme" bölümlerine dahildir. Bu konunun TestLanguageService kullandığı MyLanguageService ' i kullanın.

### <a name="the-parser-and-scanner"></a>Ayrıştırıcı ve tarayıcı

1. [Eski dil hizmeti ayrıştırıcısı ve tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)bölümünde açıklandığı gibi, diliniz için bir Ayrıştırıcı ve tarayıcı uygulayın.

     Ayrıştırıcınızı nasıl uygulayacağınızı ve tarayıcınızı tamamen siz yapın ve bu konunun kapsamını aşın.

## <a name="language-service-features"></a>Dil hizmeti özellikleri
 Dil hizmetindeki her bir özelliği uygulamak için, genellikle uygun MPF dil hizmeti sınıfından bir sınıf türetirsiniz, gereken tüm soyut yöntemleri uygular ve uygun yöntemleri geçersiz kılabilirsiniz. Oluşturduğunuz ve/veya türettiğiniz sınıflar, desteklemeyi düşündüğünüz özelliklere bağımlıdır. Bu özellikler, [eski dil hizmeti özelliklerinde](../../extensibility/internals/legacy-language-service-features1.md)ayrıntılı olarak ele alınmıştır. Aşağıdaki yordam, MPF sınıflarından bir sınıfı türetmeye yönelik genel yaklaşımdır.

#### <a name="deriving-from-an-mpf-class"></a>MPF sınıfından türetme

1. **Çözüm Gezgini**' de, VSPackage projesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin.

2. Şablon listesinde **sınıfın** seçildiğinden emin olun.

     Sınıf dosyası için uygun bir ad girin ve **Ekle**' ye tıklayın.

3. Yeni sınıf dosyasında aşağıdaki `using` yönergeleri ekleyin.

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs" id="Snippet4":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb" id="Snippet4":::

4. İstenen MPF sınıfından türetmek için sınıfı değiştirin.

5. Temel sınıfın oluşturucusuyla aynı parametreleri alan ve Oluşturucu parametrelerini temel sınıf oluşturucusuna geçiren bir sınıf oluşturucu ekleyin.

     Örneğin, sınıftan türetilmiş bir sınıf için Oluşturucu <xref:Microsoft.VisualStudio.Package.Source> aşağıdaki gibi görünebilir:

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs" id="Snippet5":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb" id="Snippet5":::

6. **Düzen**, **IntelliSense** menüsünde, temel sınıfta uygulanması gereken herhangi bir soyut yöntem varsa, **Özet sınıfını Uygula** ' yı seçin.

7. Aksi takdirde, giriş işaretini sınıfın içine konumlandırın ve geçersiz kılınacak yöntemi girin.

     Örneğin, `public override` Bu sınıfta geçersiz kılınabilen tüm yöntemlerin listesini görmek için yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

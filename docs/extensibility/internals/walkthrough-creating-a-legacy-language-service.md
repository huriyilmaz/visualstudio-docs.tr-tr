---
title: 'Walkthrough: Eski Dil Hizmeti Oluşturma | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703695"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>İzlenecek Yol: Eski Dil Hizmeti Oluşturma
Bir dil hizmetini [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] uygulamak için yönetilen paket çerçevesi (MPF) dil sınıflarını kullanmak kolaydır. Dil hizmetini, dil hizmetini barındıracak bir VSPackage'a ve diliniz için bir aranıza ihtiyacınız vardır.

## <a name="prerequisites"></a>Ön koşullar
 Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'ya](../../extensibility/visual-studio-sdk.md)bakın.

## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Paket Proje Şablonu için Konumlar
 Visual Studio Package Project Template, **Yeni Proje** iletişim kutusunda üç farklı şablon noktasında bulunabilir:

1. Visual Basic Extensibility altında. Projenin varsayılan dili Visual Basic'tir.

2. C# Genişletilebilirlik altında. Projenin varsayılan dili C#'dır.

3. Diğer Proje Türleri Altında Genişletilebilirlik. Projenin varsayılan dili C++'dır.

### <a name="create-a-vspackage"></a>VSPackage Oluşturma

1. Visual Studio Package proje şablonuyla yeni bir VSPackage oluşturun.

    Varolan bir VSPackage'a bir dil hizmeti ekliyorsanız, aşağıdaki adımları atlayın ve doğrudan "Dil Hizmeti Sınıfı Oluştur" yordamına gidin.

2. Projenin adı için MyLanguagePackage'ı girin ve **Tamam'ı**tıklatın.

    İstediğin ismi kullanabilirsin. Burada ayrıntılı olarak ayrıntılı olarak bu yordamlar isim olarak MyLanguagePackage varsayalım.

3. Dil [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] olarak ve yeni bir anahtar dosyası oluşturmak için seçenek olarak seçin. **İleri**’ye tıklayın.

4. Uygun şirket ve paket bilgilerini girin. **İleri**’ye tıklayın.

5. **Menü Komutunu**seçin. **İleri**’ye tıklayın.

    Kod parçacıklarını desteklemek istemiyorsanız, Bitiş'i tıklatıp bir sonraki adımı yok sayabilirsiniz.

6. **Komut Adı** ve `cmdidInsertSnippet` **Komut Kimliği**için Ekle **Snippet** girin. **Son**'a tıklayın.

    **Komut Adı** ve **Komut Kimliği** ne isterseniz olabilir, bunlar sadece örneklerdir.

### <a name="create-the-language-service-class"></a>Dil Hizmeti Sınıfını Oluşturma

1. **Solution Explorer'da**MyLanguagePackage projesine sağ tıklayın, **Ekle**, **Başvuru**ekle'yi seçin ve ardından **Yeni Başvuru Ekle** düğmesini seçin.

2. Başvuru **Ekle** iletişim kutusunda, **.NET** sekmesinde **Microsoft.VisualStudio.Package.LanguageService'i** seçin ve **Tamam'ı**tıklatın.

     Bu dil paketi projesi için yalnızca bir kez yapılmalıdır.

3. **Solution Explorer'da,** VSPackage projesine sağ tıklayın ve **Ekle**, **Sınıf'** ı seçin.

4. **Şablonlar** listesinde Sınıf seçildiğinden emin olun.

5. Sınıf dosyasının adı için **MyLanguageService.cs** girin ve **Ekle'yi**tıklatın.

     İstediğin ismi kullanabilirsin. Burada ayrıntılı olarak `MyLanguageService` belirtilen bu yordamlar ad olarak kabul edin.

6. MyLanguageService.cs dosyasına aşağıdaki `using` yönergeleri ekleyin.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Sınıftan `MyLanguageService` türeecek sınıfı <xref:Microsoft.VisualStudio.Package.LanguageService> değiştirin:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. İmleci "LanguageService" üzerine yerleştirin ve **Edit**, **IntelliSense** menüsünden **Soyut Sınıfı Uygula'yı**seçin. Bu, bir dil hizmeti sınıfını uygulamak için gerekli en az yöntemi ekler.

9. Eski Dil Hizmeti Nin Uygulanmasında açıklandığı gibi soyut yöntemleri [uygulayın.](../../extensibility/internals/implementing-a-legacy-language-service2.md)

### <a name="register-the-language-service"></a>Dil Servisini Kaydedin

1. MyLanguagePackagePackage.cs dosyasını açın ve `using` aşağıdaki yönergeleri ekleyin:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Eski Dil Hizmeti Kaydı'nda açıklandığı gibi dil hizmeti sınıfınızı [kaydedin.](../../extensibility/internals/registering-a-legacy-language-service1.md) Bu, ProvideXX özniteliklerini ve "Dil Hizmeti sunma" bölümlerini içerir. Bu konunun TestLanguageService kullandığı MyLanguageService'i kullanın.

### <a name="the-parser-and-scanner"></a>Parser ve Tarayıcı

1. [Eski Dil Hizmeti Parser](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)ve Scanner'da açıklandığı gibi diliniz için bir arave tarayıcı uygulayın.

     Nasıl ayrıştırıcı ve tarayıcı uygulamak tamamen size kalmış ve bu konunun kapsamı dışındadır.

## <a name="language-service-features"></a>Dil Hizmeti Özellikleri
 Dil hizmetindeki her özelliği uygulamak için, genellikle uygun MPF dil hizmeti sınıfından bir sınıf türedersiniz, gerektiğinde soyut yöntemler uygular ve uygun yöntemleri geçersiz kılarsınız. Hangi sınıflar oluşturduğunuz ve/veya türetettiğiniz, desteklemeyi planladığınız özelliklere bağlıdır. Bu özellikler Eski Dil Hizmeti Özellikleri'nde ayrıntılı olarak ele [alınmıştır.](../../extensibility/internals/legacy-language-service-features1.md) Aşağıdaki yordam, MPF sınıflarından bir sınıf türetmek için genel bir yaklaşımdır.

#### <a name="deriving-from-an-mpf-class"></a>MPF Sınıfından Türeyen

1. **Solution Explorer'da,** VSPackage projesine sağ tıklayın ve **Ekle**, **Sınıf'** ı seçin.

2. **Şablonlar** listesinde Sınıf seçildiğinden emin olun.

     Sınıf dosyası için uygun bir ad girin ve **Ekle'yi**tıklatın.

3. Yeni sınıf dosyasında aşağıdaki `using` yönergeleri ekleyin.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. İstenilen MPF sınıfından türeecek sınıfı değiştirin.

5. Taban sınıfın oluşturucusuyla en az aynı parametreleri alan bir sınıf oluşturucu ekleyin ve oluşturucu parametrelerini taban sınıf oluşturucuya geçirin.

     Örneğin, <xref:Microsoft.VisualStudio.Package.Source> sınıftan türetilen bir sınıfın oluşturucusu aşağıdaki gibi görünebilir:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. **Edit**, **IntelliSense** menüsünden, taban sınıfın uygulanması gereken soyut yöntemleri varsa **Soyut Sınıfı Uygula'yı** seçin.

7. Aksi takdirde, caret'i sınıfın içine yerleştirin ve geçersiz kılınacak yöntemi girin.

     Örneğin, bu `public override` sınıfta geçersiz kılınabilecek tüm yöntemlerin listesini görmek için yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

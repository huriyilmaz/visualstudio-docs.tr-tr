---
title: 'İzlenecek yol: eski dil hizmeti oluşturma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba09df818b95ac96f2092685ce4100873a18a05f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647989"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>İzlenecek Yol: Eski Dil Hizmeti Oluşturma
@No__t_0 dil hizmetini uygulamak için yönetilen paket çerçevesi (MPF) dil sınıflarını kullanmak basittir. Dil hizmetini, dil hizmetini ve diliniz için bir ayrıştırıcısı barındırmak üzere bir VSPackage gerekir.

## <a name="prerequisites"></a>Prerequisites
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio paketi proje şablonu konumları
 Visual Studio paketi proje şablonu, **Yeni proje** iletişim kutusunda üç farklı şablon konumu içinde bulunabilir:

1. Visual Basic genişletilebilirlik altında. Projenin varsayılan dili Visual Basic.

2. Genişletilebilirlik C# altında. Projenin varsayılan dili C#.

3. Diğer proje türleri genişletilebilirliği altında. Projenin varsayılan dili C++.

### <a name="create-a-vspackage"></a>VSPackage oluşturma

1. Visual Studio Package proje şablonuyla yeni bir VSPackage oluşturun.

    Var olan bir VSPackage 'a dil hizmeti ekliyorsanız, aşağıdaki adımları atlayın ve doğrudan "dil hizmeti sınıfı oluşturma" yordamına gidin.

2. Projenin adı için MyLanguagePackage girin ve **Tamam**' a tıklayın.

    Dilediğiniz adı kullanabilirsiniz. Burada ayrıntılı olarak, ad olarak MyLanguagePackage varsayılır.

3. Dil olarak [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] ' ı ve yeni bir anahtar dosyası oluşturma seçeneğini belirleyin. **İleri**'ye tıklayın.

4. Uygun şirket ve paket bilgilerini girin. **İleri**'ye tıklayın.

5. **Menü komutunu**seçin. **İleri**'ye tıklayın.

    Kod parçacıklarını desteklemeyi düşünmüyorsanız, yalnızca son ' a tıklayabilir ve sonraki adımı yoksayabilirsiniz.

6. Komut adı olarak, komut **adı** ve `cmdidInsertSnippet` **Ekle kod parçacığını** **girin.** **Son**'a tıklayın.

    **Komut adı** ve **komut kimliği** istediğiniz şey olabilir. bunlar yalnızca örnektir.

### <a name="create-the-language-service-class"></a>Dil hizmeti sınıfını oluşturma

1. **Çözüm Gezgini**, MyLanguagePackage projesine sağ tıklayın, **Ekle**, **başvuru**ve ardından **Yeni Başvuru Ekle** düğmesini seçin.

2. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesinde **Microsoft. VisualStudio. Package. LanguageService** ' i seçin ve **Tamam**' ı tıklatın.

     Bu, dil paketi projesi için yalnızca bir kez yapılmalıdır.

3. **Çözüm Gezgini**' de, VSPackage projesine sağ tıklayın ve **Ekle**, **sınıf**' i seçin.

4. Şablon listesinde **sınıfın** seçildiğinden emin olun.

5. Sınıf dosyasının adı için **MyLanguageService.cs** girin ve **Ekle**' ye tıklayın.

     Dilediğiniz adı kullanabilirsiniz. Burada ayrıntılı olan bu yordamlar ad olarak `MyLanguageService` varsayar.

6. MyLanguageService.cs dosyasında aşağıdaki `using` yönergelerini ekleyin.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. @No__t_1 sınıfından türetmek için `MyLanguageService` sınıfını değiştirin:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. İmleci "LanguageService" üzerine konumlandırın ve **Düzenle**, **IntelliSense** menüsünde, **soyut sınıf Uygula**' yı seçin. Bu, dil hizmeti sınıfını uygulamak için gereken en düşük yöntemleri ekler.

9. [Eski dil hizmetini uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)bölümünde açıklandığı gibi soyut yöntemleri uygulayın.

### <a name="register-the-language-service"></a>Dil hizmetini kaydetme

1. MyLanguagePackagePackage.cs dosyasını açın ve aşağıdaki `using` yönergeleri ekleyin:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

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

3. Yeni sınıf dosyasında aşağıdaki `using` yönergelerini ekleyin.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. İstenen MPF sınıfından türetmek için sınıfı değiştirin.

5. Temel sınıfın oluşturucusuyla aynı parametreleri alan ve Oluşturucu parametrelerini temel sınıf oluşturucusuna geçiren bir sınıf oluşturucu ekleyin.

     Örneğin, <xref:Microsoft.VisualStudio.Package.Source> sınıftan türetilmiş bir sınıf için Oluşturucu aşağıdaki gibi görünebilir:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. **Düzen**, **IntelliSense** menüsünde, temel sınıfta uygulanması gereken herhangi bir soyut yöntem varsa, **Özet sınıfını Uygula** ' yı seçin.

7. Aksi takdirde, giriş işaretini sınıfın içine konumlandırın ve geçersiz kılınacak yöntemi girin.

     Örneğin, bu sınıfta geçersiz kılınabilen tüm yöntemlerin listesini görmek için `public override` yazın.

## <a name="see-also"></a>Ayrıca Bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

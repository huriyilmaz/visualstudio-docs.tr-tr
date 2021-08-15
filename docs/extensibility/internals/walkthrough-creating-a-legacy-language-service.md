---
title: 'Kılavuz: Eski Dil Hizmeti Oluşturma | Microsoft Docs'
description: Visual C# dilinde dil hizmeti uygulamak için yönetilen paket çerçevesi dil sınıflarını kullanmayı öğrenin.
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
ms.openlocfilehash: 2aafa7c3040534c075d5911d36dd2486c60122955dc51f28e71960b43513fff3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321291"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>İzlenecek yol: Eski Dil Hizmeti oluşturma
içinde bir dil hizmeti uygulamak için yönetilen paket çerçevesi (MPF) dil sınıflarını [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] kullanmak oldukça kolaydır. Dil hizmetini, dil hizmetinin kendisini ve diliniz için ayrıştırıcıyı barındırmak için bir VSPackage gerekir.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu takip etmek için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK.](../../extensibility/visual-studio-sdk.md)

## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Package Project Için Konumlar
 Paket Visual Studio Paketi Project Şablonu, Yeni Uygulama iletişim kutusunda üç **farklı şablon Project** bulunabilir:

1. Genişletilebilirlik Visual Basic altında. Projenin varsayılan dili Visual Basic.

2. C# Genişletilebilirliği altında. Projenin varsayılan dili C# dilidir.

3. Diğer Project Türleri Genişletilebilirliği. Projenin varsayılan dili C++ dilidir.

### <a name="create-a-vspackage"></a>VSPackage oluşturma

1. Visual Studio Package proje şablonuyla yeni bir VSPackage oluşturun.

    Var olan bir VSPackage'a dil hizmeti ekliyorsanız, aşağıdaki adımları atlayıp doğrudan "Dil Hizmeti Sınıfı Oluşturma" yordamına gidin.

2. Projenin adı olarak MyLanguagePackage girin ve Tamam'a **tıklayın.**

    Istediğiniz adı kullanabilirsiniz. Burada ayrıntılı olarak açıklanan bu yordamlarda adı MyLanguagePackage olduğu varsayıldı.

3. Dil [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] olarak seçin ve yeni bir anahtar dosyası oluşturma seçeneğini belirleyin. **İleri**’ye tıklayın.

4. Uygun şirket ve paket bilgilerini girin. **İleri**’ye tıklayın.

5. Menü **Komutu'na tıklayın.** **İleri**’ye tıklayın.

    Kod parçacıklarını desteklemeyi amacınız yoksa Son'a tıklar ve sonraki adımı yoksayabilirsiniz.

6. Komut **Adı olarak** Kod Parçacığı Ekle **ve** Komut Kimliği `cmdidInsertSnippet` için **girin.** **Finish (Son)** düğmesine tıklayın.

    Komut **Adı** ve **Komut Kimliği** istediğiniz gibi olabilir, bunlar yalnızca örnektir.

### <a name="create-the-language-service-class"></a>Dil Hizmeti Sınıfı Oluşturma

1. Bu **Çözüm Gezgini,** MyLanguagePackage projesine sağ tıklayın, **Ekle,** **Başvuru'ya** tıklayın ve ardından Yeni Başvuru **Ekle düğmesini** seçin.

2. Başvuru Ekle **iletişim kutusunda,** .NET sekmesinde **Microsoft.VisualStudio.Package.LanguageService** öğesini seçin **ve Tamam'a** **tıklayın.**

     Bu, dil paketi projesi için yalnızca bir kez yapılması gerekir.

3. Bu **Çözüm Gezgini** VSPackage projesine sağ tıklayın ve Ekle , **Sınıf'ı** **seçin.**

4. Şablonlar **listesinde Sınıf'ın** seçili olduğundan emin olun.

5. Sınıf **dosyasının adı olarak MyLanguageService.cs** girin ve Ekle'ye **tıklayın.**

     Istediğiniz adı kullanabilirsiniz. Burada açıklanan bu yordamların `MyLanguageService` adı olarak kabul edilen yordamlar vardır.

6. MyLanguageService.cs dosyasına aşağıdaki yönergeleri `using` ekleyin.

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs" id="Snippet1":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb" id="Snippet1":::

7. sınıfından `MyLanguageService` türetilen sınıfını <xref:Microsoft.VisualStudio.Package.LanguageService> değiştirme:

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguageservice.cs" id="Snippet2":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguageservice.vb" id="Snippet2":::

8. İmleci "LanguageService" üzerine getirin ve **Düzenle**, **IntelliSense** menüsünden Soyut Sınıf **Uygulay'ı seçin.** Bu, dil hizmeti sınıfı uygulamak için gereken en düşük yöntemleri ekler.

9. Soyut yöntemleri, Eski Dil Hizmeti [Uygulama konusunda açıklandığı gibi uygulama.](../../extensibility/internals/implementing-a-legacy-language-service2.md)

### <a name="register-the-language-service"></a>Dil Hizmeti'ne kaydolma

1. MyLanguagePackagePackage.cs dosyasını açın ve aşağıdaki `using` yönergeleri ekleyin:

     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mylanguagepackagepackage.vb" id="Snippet3":::
     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mylanguagepackagepackage.cs" id="Snippet3":::

2. Eski Dil Hizmetini Kaydetme konusunda açıklandığı [gibi dil hizmeti sınıfınızı kaydetme.](../../extensibility/internals/registering-a-legacy-language-service1.md) Bu, ProvideXX özniteliklerini ve "Dil Hizmetini Sağlama" bölümlerini içerir. Bu konu başlığında TestLanguageService'in bulunduğu MyLanguageService kullanın.

### <a name="the-parser-and-scanner"></a>Ayrıştırıcı ve Tarayıcı

1. Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcı'da açıklandığı gibi diliniz için bir [ayrıştırıcı ve tarayıcı uygulama.](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

     Ayrıştırıcınızı ve tarayıcınızı uygulamanız tamamen size bağlı ve bu konunun kapsamının dışındadır.

## <a name="language-service-features"></a>Dil Hizmeti Özellikleri
 Dil hizmetlerinde her özelliği uygulamak için, genellikle uygun MPF dil hizmeti sınıfından bir sınıf türetir, gerekli soyut yöntemleri uygulamak ve uygun yöntemleri geçersiz kılar. Hangi sınıfları oluşturabilirsiniz ve/veya hangi sınıflardan türetilen, desteklemekte olduğunuz özelliklere bağlıdır. Bu özellikler Eski Dil Hizmeti [Özellikleri'ne ayrıntılı olarak anlatılmıştır.](../../extensibility/internals/legacy-language-service-features1.md) Aşağıdaki yordam, MPF sınıflarından bir sınıf türetme genel yaklaşımıdır.

#### <a name="deriving-from-an-mpf-class"></a>MPF Sınıfından Türetme

1. Bu **Çözüm Gezgini** VSPackage projesine sağ tıklayın ve Ekle , **Sınıf'ı** **seçin.**

2. Şablonlar **listesinde Sınıf'ın** seçili olduğundan emin olun.

     Sınıf dosyası için uygun bir ad girin ve **Ekle'ye tıklayın.**

3. Yeni sınıf dosyasına aşağıdaki yönergeleri `using` ekleyin.

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs" id="Snippet4":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb" id="Snippet4":::

4. İstenen MPF sınıfından türetilen sınıfını değiştirme.

5. En azından temel sınıfın oluşturucus ile aynı parametreleri alan ve üzerinde oluşturucu parametrelerini temel sınıf oluşturucuya iletir bir sınıf oluşturucu ekleyin.

     Örneğin, sınıfından türetilen bir sınıfın <xref:Microsoft.VisualStudio.Package.Source> oluşturucusu aşağıdaki gibi olabilir:

     :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/cs/mysource.cs" id="Snippet5":::
     :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/creatingalanguageservice(managedpackageframework)/vb/mysource.vb" id="Snippet5":::

6. Temel **sınıfta** uygulanması gereken soyut  yöntemler varsa Düzenle , **IntelliSense** menüsünden Soyut Sınıf Uygulay'ı seçin.

7. Aksi takdirde, giriş imtiyazını sınıfın içine getirin ve geçersiz kılınan yöntemi girin.

     Örneğin, bu `public override` sınıfta geçersiz kılınabilir tüm yöntemlerin listesini görmek için yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

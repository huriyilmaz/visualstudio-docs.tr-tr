---
title: SharePoint uygulamalarının performansının profilini oluşturma | Microsoft Docs
description: Yavaş veya yeterince uygun çalışıyorsa SharePoint uygulamalarının performansını profil halinde yapın. Sorunlu kodu bulmak için Visual Studio profil oluşturma özelliklerini kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d59f5b472f791f9774515cdb3e92cc4cf7f9f55b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860743"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>SharePoint uygulamalarının performansını profil halinde

SharePoint uygulamalarınız yavaş veya yeterince uygun bir şekilde yapılıyorsa, sorunlu kodu ve diğer öğeleri belirlemek için Visual Studio 'daki profil oluşturma özelliklerini kullanabilirsiniz. Yük testi özelliğini kullanarak, çok sayıda kullanıcının uygulamaya aynı anda erişmesi gibi bir SharePoint uygulamasının stres altında nasıl gerçekleştiğini belirleyebilirsiniz. Web performans testlerini çalıştırarak, uygulamanın Web üzerinde nasıl gerçekleştiğini ölçebilir. Kodlanmış UI testlerini kullanarak, Kullanıcı arabirimi de dahil olmak üzere tüm SharePoint uygulamasının düzgün çalışıp çalışmadığını doğrulayabilirsiniz. Bu testleri birlikte kullandığınızda, uygulamanızı dağıtmadan önce performans sorunlarını belirlemenize yardımcı olabilirler.

## <a name="profile-tools-overview"></a>Profil araçlarına genel bakış

Profil oluşturma, uygulama çalışırken uygulamanızın performans davranışını gözlemleme ve kaydetme sürecini ifade eder. Uygulamanızın profilini oluşturarak performans sorunlarını, verimsiz kodu ve bellek ayırma sorunlarını, uygulamaların yavaş çalışmasına veya çok fazla bellek kullanmasına neden olan sorunları ortaya çıkarabilir. Örneğin, kodunuzun içindeki etkin noktaları belirlemek için profil oluşturmayı kullanabilirsiniz. Bu, sık çağrılan kod kesimleri olan ve uygulamanızın genel performansını yavaşlatabilecek bir kod kesimi olabilir. Etkin noktaları tanımladıktan sonra, bunları genellikle iyileştirebilirsiniz veya ortadan kaldırabilirsiniz.

Bu tür performans sorunlarını belirlemek ve bulmak için tümleşik geliştirme ortamında (IDE) birkaç profil oluşturma aracı kullanabilirsiniz. Bu araçlar, diğer Visual Studio projelerinde olduğu gibi SharePoint projeleri için de aynı şekilde çalışır. Profil Oluşturma Araçları Performans Sihirbazı, belirttiğiniz testleri kullanan bir performans oturumu oluşturma konusunda size yol gösterir. Bir performans oturumu, bir veya daha fazla profil oluşturma çalıştırmalarının sonuçlarıyla birlikte, bir uygulamadan performans bilgilerini toplamak için kullanılan yapılandırma verileri kümesidir. Performans oturumları proje klasörünüzde depolanır ve bunları **Performans Gezgini** görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [performans toplama yöntemlerini anlama](../profiling/understanding-performance-collection-methods.md).

Uygulamanızda bir profil analizi oluşturup çalıştırdıktan sonra, bir rapor, performansına ilişkin ayrıntıları sağlar. Bu rapor, zaman içinde CPU kullanımının bir grafiği, hiyerarşik bir işlev çağrı yığını veya bir çağrı ağacı gibi öğeleri içerebilir. Raporun tam içerikleri, çalıştırdığınız test türüne bağlı olarak (örnekleme veya izleme gibi) farklılık gösterebilir. Daha fazla bilgi için bkz. [profil oluşturma araçları rapora genel bakış](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Performans oturumu işlemi

Bir uygulama profili oluşturmak için, performans oturumu oluşturmak üzere Profil Oluşturma Araçları Performans Sihirbazı 'Nı kullanarak başlar. Menü çubuğunda **Çözümle**, **performans Başlatma Sihirbazı**' nı seçin. Sihirbazı tamamladıktan sonra, istediğiniz profil yöntemi ve profil vermek istediğiniz uygulama gibi performans oturumunuz için gerekli bilgileri girersiniz. Daha fazla bilgi için bkz. [nasıl yapılır: performans sihirbazını kullanarak Web sitesi veya Web uygulaması profili oluşturma](../profiling/how-to-collect-performance-data-for-a-web-site.md). Alternatif olarak, bir performans oturumu ayarlamak ve çalıştırmak için komut satırı seçeneklerini kullanabilirsiniz. Daha fazla bilgi için, bkz. [komut satırından profil oluşturma araçları kullanma](../profiling/using-the-profiling-tools-from-the-command-line.md). Bir performans oturumunun her yönünü el ile yapılandırmak istiyorsanız, bkz. [nasıl yapılır: el ile profil oluşturma araçları performans oturumları oluşturma](../profiling/how-to-manually-create-performance-sessions.md). Ayrıca, **test sonuçları** penceresinde, birim testinin kısayol menüsünü açarak ve ardından **performans oturumu oluştur**' u seçerek bir birim testten bir performans oturumu oluşturabilirsiniz.

Bir performans oturumu ayarladıktan sonra oturum yapılandırması kaydedilir, sunucu profil oluşturma verileri sağlamak üzere yapılandırılır ve uygulama çalışır. Uygulamayı kullanırken, performans verileri bir günlük dosyasına yazılır. Performans oturumları, **hedefler** klasörü altında **Performans Gezgini** listelenmiştir. Bir performans oturumu bittikten sonra, raporu **Performans Gezgini** **rapor klasöründe görüntülenir** . Raporu göstermek için **Performans Gezgini** açın. Bir performans oturumunun özelliklerini görüntülemek veya yapılandırmak için, **Performans Gezgini** kısayol menüsünü açın ve ardından **Özellikler**' i seçin. Bir performans oturumunun belirli özellikleri hakkında daha fazla bilgi için bkz. [profil oluşturma araçları performans oturumlarını yapılandırma](../profiling/configuring-performance-sessions.md). Bir performans oturumunun sonuçlarını yorumlama hakkında daha fazla bilgi için bkz. [profil oluşturma araçları verileri çözümleme](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Stres testi

Visual Studio 'da yük testleri ve Web performans testleri oluşturarak uygulamalarınızın stres performansını çözümleyebilirsiniz. Visual Studio 'da bir yük testi oluşturduğunuzda, uygulamanızı test etmek için senaryo olarak adlandırılan faktörlerin bir bileşimini belirtirsiniz. Bu faktörlere yük modeli, test karışımı modeli, test karışımı, ağ karışımı ve Web tarayıcısı karışımı dahildir. Yük testi senaryoları, hem birim testlerini hem de Web performans testlerini içerebilir.

Şekil 1: yük testi sonuçları örneği

![Yük testi grafik görünümünü çalıştırma](../sharepoint/media/load-webgraphs.png "Yük testi grafik görünümünü çalıştırma")

Web performans testleri, son kullanıcının bir SharePoint uygulamasıyla nasıl etkileşime girebileceğini taklit eder. HTTP isteklerini bir tarayıcı oturumunda kaydederek veya **Web performans testi Kaydedicisi**' ni kullanarak Web performans testleri oluşturabilirsiniz. Web istekleri, tarayıcı oturumu bittikten sonra **Web Performans Testi Düzenleyicisi** görüntülenir. Daha sonra **Web performans test sonuçları görüntüleyicisindeki** sonuçlarda hata ayıklaması yapabilirsiniz. Ayrıca, **Web Performans Testi Düzenleyicisi** kullanarak Web performans testlerini el ile oluşturabilirsiniz.

## <a name="test-user-interfaces"></a>Test Kullanıcı arabirimleri

Kodlanmış UI testleri, SharePoint uygulamanızı Kullanıcı arabirimi (UI) üzerinden otomatik olarak ister. Bu sınamalar, doğru şekilde çalıştıklarından emin olmak için düğme ve menü gibi UI denetimlerini kapsar. Bu tür bir test, Kullanıcı arabiriminde (örneğin, bir Web sayfasında) doğrulama veya başka bir mantık gerçekleştirildiğinde özellikle yararlıdır. Ayrıca, el ile testleri otomatikleştirmek için kodlanmış UI testleri de kullanabilirsiniz. SharePoint uygulamalarınız için kodlanmış UI testleri, diğer uygulama türleri için testler oluştururken aynı şekilde oluşturulur. Daha fazla bilgi için bkz. [KODLANMıŞ UI Testleriyle SharePoint 2010 uygulamalarını test etme](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: SharePoint uygulaması profili oluşturma](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Bir SharePoint uygulamasında örnekleme profili analizinin nasıl gerçekleştirileceğini gösterir.|
|[Uygulamadan önce uygulamanızı performans testi](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts&preserve-view=true)|Test SharePoint uygulamalarını vurgulamada yardımcı olan yük testlerinin nasıl oluşturulduğunu açıklar.|
|[Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)|Birim testlerini kullanarak kodunuzda mantık hatalarının nasıl bulunacağını açıklar.|
|[Kodlanmış UI Testleriyle SharePoint 2010 Uygulamalarını Test Etme](/previous-versions/visualstudio/visual-studio-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests?preserve-view=true&view=vs-2015)|SharePoint uygulamalarınızın Kullanıcı arabiriminin nasıl test edileceğini açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümlerini derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Kod Kalitesini Geliştirme](../test/improve-code-quality.md)
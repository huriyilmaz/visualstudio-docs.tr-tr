---
title: SharePoint Çözümlerinde hata ayıklama | Microsoft Docs
description: Visual Studio hata ayıklayıcısını kullanarak SharePoint Çözümlerinde hata ayıklayın. F5 hata ayıklama ve dağıtım sürecini, hata ayıklama iş akışlarını ve hata ayıklama özelliği olay alıcılarını keşfet.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c0bd1996f5d42561cb2d44879ab702d6b6c4b4f7
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672866"
---
# <a name="debug-sharepoint-solutions"></a>SharePoint Çözümlerinde hata ayıklama
  Hata ayıklayıcıyı kullanarak SharePoint Çözümlerinde hata ayıklaması yapabilirsiniz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Hata ayıklamayı başlattığınızda, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Proje dosyalarını SharePoint sunucusuna dağıtır ve ardından Web tarayıcısında SharePoint sitesinin bir örneğini açar. Aşağıdaki bölümlerde ' de SharePoint uygulamalarının nasıl ayıklanacağı açıklanmaktadır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Hata ayıklamayı etkinleştir](#enable-debugging)

- [F5 hata ayıklama ve dağıtım işlemi](#f5-debug-and-deployment-process)

- [SharePoint proje özellikleri](#sharepoint-project-features)

- [İş akışları hata ayıklama](#debug-workflows)

- [Hata ayıklama özelliği olay alıcıları](#debug-feature-event-receivers)

- [Ehanced hata ayıklama bilgilerini etkinleştir](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Hata ayıklamayı etkinleştir
 İçindeki bir SharePoint çözümünde ilk kez hata ayıklarken [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , bir iletişim kutusu web.config dosyanın hata ayıklamayı etkinleştirmek üzere yapılandırılmadığını uyarır. (web.config dosyası SharePoint Server 'ı yüklediğinizde oluşturulur. Daha fazla bilgi için bkz. [Web.config dosyalarla çalışma](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)).) İletişim kutusu, hata ayıklamayı etkinleştirmek için projeyi hata ayıklamadan çalıştırma veya web.config dosyasını değiştirme seçeneğini sunar. İlk seçeneği belirlerseniz, proje normal şekilde çalışır. İkinci seçeneği belirlerseniz, web.config dosyası şu şekilde yapılandırılır:

- Çağrı yığınını aç ( `CallStack="true"` )

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]() İçinde özel hataları devre dışı bırak `<customErrors mode="Off" />`

- Derleme hata ayıklamasını etkinleştir ( `<compilation debug="true">` )

  Elde edilen web.config dosyası şu şekildedir:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 Değişiklikleri tersine çevirmek ve hata ayıklamayı devre dışı bırakmak için [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] web.config dosyasında aşağıdakini değiştirin:

- Çağrı yığınını kapat ( `CallStack="false"` )

- [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]() İçinde özel hataları `<customErrors mode="On" />` Etkinleştir

- Derleme hata ayıklamasını devre dışı bırak ( `<compilation debug="false">` )

## <a name="f5-debug-and-deployment-process"></a>F5 hata ayıklama ve dağıtım işlemi
 SharePoint projenizi hata ayıklama modunda çalıştırdığınızda, SharePoint dağıtım işlemi aşağıdaki görevleri gerçekleştirir:

1. Özelleştirilebilir dağıtım öncesi komutlarını çalıştırır.

2. Komutları kullanarak bir Web çözüm paketi (. wsp) dosyası oluşturur [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] . . Wsp dosyası tüm gerekli dosya ve özellikleri içerir. Daha fazla bilgi için bkz. [çözümlere genel bakış](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. SharePoint çözümü bir grup çözümüdür, [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] belirtilen site için uygulama havuzunu geri dönüştürür [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] . Bu adım, çalışan işlemi tarafından kilitlenen dosyaları yayınlar [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] .

4. Paketin önceki bir sürümü zaten mevcutsa,. wsp dosyasındaki özellik ve dosyaların önceki sürümünü geri çeker. Bu adım özellikleri devre dışı bırakır, çözüm paketini kaldırır ve ardından SharePoint sunucusundaki çözüm paketini siler.

5. . Wsp dosyasındaki özelliklerin ve dosyaların geçerli sürümünü yüklenir. Bu adım, çözümü SharePoint sunucusuna ekler ve kurar.

6. İş akışları için iş akışı derlemesini yüklenir. *Derleme konumu* özelliğini kullanarak konumunu değiştirebilirsiniz.

7. Kapsam site veya Web ise, projenin SharePoint 'teki özelliğini etkinleştirir. Grup ve WebApplication kapsamlarında özellikler etkinleştirilmemiş.

8. İş akışları için, iş akışını **SharePoint Özelleştirme Sihirbazı**'Nda seçtiğiniz SharePoint kitaplığı, liste veya siteyle ilişkilendirir.

   > [!NOTE]
   > Bu ilişki yalnızca, sihirbazda **iş akışını otomatik olarak ilişkilendir** ' i seçtiyseniz oluşur.

9. Özelleştirilebilir dağıtım sonrası komutlarını çalıştırır.

10. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Hata ayıklayıcıyı [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] işleme iliştirir (*w3wp.exe*). Proje türü, *Korumalı çözüm* özelliğini değiştirmenize izin verir ve değeri **true** olarak ayarlanırsa, hata ayıklayıcı farklı bir işleme (*SPUCWorkerProcess.exe*) iliştirir. Daha fazla bilgi için bkz. [Korumalı çözüm konuları](../sharepoint/sandboxed-solution-considerations.md).

11. SharePoint çözümü bir grup çözümüdür ise JavaScript hata ayıklayıcıyı başlatır.

12. Web tarayıcısında uygun kitaplığı, listeyi veya site sayfasını görüntüler.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Her görev tamamlandıktan sonra çıkış penceresinde bir durum iletisi görüntüler. Bir görev tamamlandıysa, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hata listesi penceresinde bir hata mesajı görüntüler.

## <a name="sharepoint-project-features"></a>SharePoint proje özellikleri
 Bir özellik, site tanımlarını kullanarak sitelerin değiştirilmesini kolaylaştıran taşınabilir ve modüler bir işlev birimidir. Ayrıca, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] belirli bir kapsam için etkinleştirilenebilir ve kullanıcılara belirli bir hedef veya görev gerçekleştirmenize yardımcı olan bir (WSS) öğeleri paketidir. Şablonlar özellik olarak dağıtılır.

 Bir projeyi hata ayıklama modunda çalıştırdığınızda, dağıtım işlemi, *%CommonProgramFiles%\Microsoft Shared\Web Server extensions\14\TEMPLATE\FEATURES* konumundaki *özellik* dizininde bir klasör oluşturur. Özellik adlarında, TestProject_Feature1 gibi _Feature *x* biçimli *Proje adı* vardır.

 Özellik dizinindeki çözümün klasörü, bir *Özellik tanım* dosyası ve bir *iş akışı Tanım* dosyası içerir. Özellik tanım dosyası (Feature.xml) projenin özelliğindeki dosyaları açıklar. proje tanım dosyası (*Elements.xml*) proje şablonunu açıklar. *Elements.xml* **Çözüm Gezgini** bulunabilir, ancak çözüm paketi oluşturulduğunda Feature.xml üretilir. Bu dosyalar hakkında daha fazla bilgi için bkz. [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>İş akışları hata ayıklama
 İş akışı projelerinde hata ayıklarken, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışı şablonunu (türüne bağlı olarak) bir kitaplığa veya listeye ekler. Daha sonra iş akışı şablonunu el ile veya bir öğe ekleyerek veya güncelleştirerek başlatabilirsiniz. Daha sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] iş akışında hata ayıklamak için kullanabilirsiniz.

> [!NOTE]
> Diğer derlemelere başvurular eklerseniz, bu derlemelerin genel derleme önbelleğinde () yüklü olduğundan emin olun [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] . Aksi takdirde, iş akışı çözümü başarısız olur. Derlemelerin nasıl yükleneceği hakkında bilgi için bkz. bir [belge veya öğe üzerinde el ile iş akışı başlatma](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Ancak, dağıtım işlemi iş akışını başlatamaz. İş akışını SharePoint Web sitesinden başlatmanız gerekir. İş akışını, Microsoft Office Word 2010 gibi bir istemci uygulaması veya ayrı sunucu tarafı kodu kullanarak da başlatabilirsiniz. **SharePoint Özelleştirme Sihirbazı**'nda belirtilen yaklaşımlardan birini kullanın.

 Örneğin, iş akışının el ile başlatılalamayacağını belirttiyseniz, iş akışını doğrudan kitaplık veya listedeki öğeden başlatın. Bir iş akışını el ile başlatma hakkında daha fazla bilgi için bkz. bir [belge öğesinde bir iş akışını el ile başlatma](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Hata ayıklama özelliği olay alıcıları
 Varsayılan olarak, bir [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint uygulaması çalıştırdığınızda, özellikleri SharePoint sunucusunda sizin için otomatik olarak etkinleştirilir. Ancak, özellik olay alıcılarından hata ayıkladığınızda bu sorunlara neden olur, çünkü bir özellik tarafından etkinleştirildiğinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , hata ayıklayıcıdan farklı bir işlemde çalışır. Bu, kesme noktaları gibi bazı hata ayıklama işlevlerinin doğru şekilde çalışmayacağı anlamına gelir.

 SharePoint 'te özelliği otomatik etkinleştirmeyi devre dışı bırakmak ve özellik olay alıcılarının düzgün şekilde hata ayıklamasını sağlamak için, hata ayıklamadan önce projenin **etkin dağıtım yapılandırma** özelliğinin değerini **etkinleştirme yok** olarak ayarlayın. Ardından, SharePoint uygulamanızda hata ayıklamaya başladıktan sonra [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , özelliği SharePoint 'te el ile etkinleştirin. Özelliği etkinleştirmek için SharePoint 'te **Site eylemleri** menüsünü açın, **site ayarları**' nı seçin, **site özelliklerini yönet** bağlantısını seçin ve ardından özelliğin yanındaki **Etkinleştir** düğmesini seçerek hata ayıklamaya normal olarak devam edin.

## <a name="enable-enhanced-debugging-information"></a>Gelişmiş hata ayıklama bilgilerini etkinleştir
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]İşlem (devenv.exe), [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ana bilgisayar işlemi (*vssphost4.exe*), SharePoint ve WCF katmanı arasındaki bazen karmaşık etkileşimler nedeniyle, oluşturma, dağıtma, vb. işlemleri yaparken oluşan hataları tanılama işlemi bir sorun olabilir. Bu tür hataları çözmenize yardımcı olması için gelişmiş hata ayıklama bilgilerini etkinleştirebilirsiniz. Bunu yapmak için, Windows kayıt defterinde aşağıdaki kayıt defteri anahtarına gidin:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 "EnableDiagnostics" **REG_DWORD** değeri zaten yoksa el ile oluşturun. "EnableDiagnostics" değerini "1" olarak ayarlayın.

 Bu anahtar değerini 1 olarak ayarlamak, üzerinde çalışırken proje sistem hataları olduğunda yığın izleme bilgilerinin **Çıkış** penceresinde görüntülenmesine neden olur [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Gelişmiş hata ayıklama bilgilerini devre dışı bırakmak için EnableDiagnostics 'i tekrar 0 olarak ayarlayın veya değeri silin.

 Diğer SharePoint kayıt defteri anahtarları hakkında daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları Için hata ayıklama uzantıları](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint Çözümlerinde Sorun giderme](../sharepoint/troubleshooting-sharepoint-solutions.md)

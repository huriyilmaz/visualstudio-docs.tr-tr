---
title: Hata Ayıklama SharePoint Çözümleri | Microsoft Docs
description: Hata SharePoint hata ayıklayıcısını kullanarak Visual Studio ayıklar. F5 hata ayıklama ve dağıtım işlemini, iş akışlarında hata ayıklamayı ve hata ayıklama özelliği olay alıcılarını keşfedin.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 63ae84fb6b7450a65962383b986625945440e432
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149331"
---
# <a name="debug-sharepoint-solutions"></a>Hata ayıklama SharePoint çözümleri
  Hata ayıklayıcıyı kullanarak SharePoint hataları [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayıklar. Hata ayıklamaya başlarken proje dosyalarını SharePoint sunucusuna dağıtır ve ardından Web tarayıcısında [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint sitenin bir örneğini açar. Aşağıdaki bölümlerde, 'de uygulama hata ayıklama SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] açıklanmaktadır.

- [Hata ayıklamayı etkinleştir](#enable-debugging)

- [F5 hata ayıklama ve dağıtım işlemi](#f5-debug-and-deployment-process)

- [SharePoint proje özellikleri](#sharepoint-project-features)

- [İş akışları hata ayıklama](#debug-workflows)

- [Hata ayıklama özelliği olay alıcıları](#debug-feature-event-receivers)

- [Hata ayıklama bilgilerini etkinleştirme](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Hata ayıklamayı etkinleştir
 içinde bir çözümde SharePoint ayıklarken, bir iletişim kutusu hata [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayıklamayı web.config dosyanın yapılandırılmamış olduğunu size belirtir. (web.config sunucusuna SharePoint oluşturulur. Daha fazla bilgi için [bkz. Web.config Dosyalarıyla Çalışma.)](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)) İletişim kutusu, hata ayıklama olmadan projeyi çalıştırma veya hata ayıklamayı etkinleştirmek için web.config değiştirme seçeneği sağlar. İlk seçeneği seçerseniz proje normal şekilde çalışır. İkinci seçeneği seçerseniz, web.config dosyası şu şekilde yapılandırılır:

- Çağrı yığınını açma ( `CallStack="true"` )

- ( ) içinde özel hataları devre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dışı `<customErrors mode="Off" />` bırakma

- Derleme hata ayıklamasını etkinleştirme ( `<compilation debug="true">` )

  Elde edilen web.config dosyası şunlardır:

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

 Değişiklikleri tersine çevirmek ve hata ayıklamayı devre dışı bırakmak için aşağıdaki [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] web.config yapın:

- Çağrı yığınını kapatma ( `CallStack="false"` )

- ( ) içinde özel [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] hataları `<customErrors mode="On" />` etkinleştirme

- Derleme hata ayıklamasını devre dışı bırakma ( `<compilation debug="false">` )

## <a name="f5-debug-and-deployment-process"></a>F5 hata ayıklama ve dağıtım işlemi
 SharePoint projenizi hata ayıklama modunda SharePoint dağıtım işlemi aşağıdaki görevleri gerçekleştirir:

1. Özelleştirilebilir dağıtım öncesi komutları çalıştırır.

2. komutlarını kullanarak bir Web çözümü paketi (.wsp) dosyası [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] oluşturur. .wsp dosyası tüm gerekli dosyaları ve özellikleri içerir. Daha fazla bilgi için bkz. [Çözümlere Genel Bakış.](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14))

3. Uygulama SharePoint bir grup çözümü ise, belirtilen site [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] için uygulama havuzunu geri dönüştürmektedir. [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] Bu adım çalışan işlemi tarafından kilitlenmiş [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] dosyaları serbest bıraktır.

4. Paketin önceki bir sürümü zaten varsa, özelliklerin ve dosyaların önceki sürümünü .wsp dosyasında geri çekin. Bu adım özellikleri devre dışı bırakılır, çözüm paketini kaldırır ve ardından çözüm paketini SharePoint siler.

5. Özelliklerin ve dosyaların geçerli sürümünü .wsp dosyasına yükleme. Bu adım çözümü SharePoint sunucusuna ekler.

6. İş akışları için iş akışı derlemesi yüklenir. Derleme Konumu özelliğini kullanarak konumunu *değiştirebilirsiniz.*

7. Kapsam Site veya Web ise SharePoint proje özelliğini etkinleştirir. Grup ve WebApplication kapsamlarında özellikler etkinleştirilmez.

8. İş akışları için, iş akışını özelleştirme sihirbazında SharePoint kitaplık, liste veya site **SharePoint ilişkilendirin.**

   > [!NOTE]
   > Bu ilişki yalnızca sihirbazda İş akışını otomatik olarak **ilişkilendirme'nin seçili** olduğu durumda gerçekleşir.

9. Özelleştirilebilir dağıtım sonrası komutlarını çalıştırır.

10. Hata [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayıklayıcıyı işleme [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (** w3wp.exe). Proje türü Korumalı Çözüm  özelliğini değiştirmenizi sağlarsa ve değeri **true** olarak ayarlanırsa hata ayıklayıcı farklı bir işleme *(* SPUCWorkerProcess.exe). Daha fazla bilgi için [bkz. Korumalı alanlı çözümde dikkat edilmesi gerekenler.](../sharepoint/sandboxed-solution-considerations.md)

11. Uygulama çözümü bir grup çözümü SharePoint JavaScript hata ayıklayıcısını başlatır.

12. Web tarayıcısında uygun kitaplığı, listeyi veya site sayfasını görüntüler.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , her görev tamamlandıktan sonra Çıkış penceresinde bir durum iletisi görüntüler. Bir görev tamamlanamadı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ise, Hata Listesi penceresinde bir hata iletisi görüntüler.

## <a name="sharepoint-project-features"></a>SharePoint proje özellikleri
 Özellik, site tanımlarını kullanarak sitelerin değiştirilmesini kolaylaştıran taşınabilir ve modüler bir işlev birimidir. Ayrıca, belirli bir kapsam için etkinleştiril WSS ve kullanıcıların belirli bir hedefi veya görevi gerçekleştirmelerini yardımcı olan [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] bir pakettir (WSS) öğeleridir. Şablonlar özellik olarak dağıtılır.

 Bir projeyi hata ayıklama modunda çalıştırsanız, dağıtım işlemi  özellik dizininde *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES* konumunda bir klasör oluşturur. Özellik adları, proje adını *x _Feature**biçimindedir,* örneğin TestProject_Feature1.

 Çözümün özellik dizinindeki klasörü bir özellik tanımı *dosyası ve* bir iş akışı *tanım dosyası* içerir. Özellik tanımı dosyası (Feature.xml), projenin Feature.The project definition file (*Elements.xml*) proje şablonunu açıklar. *Elements.xml* içinde **Çözüm Gezgini,** ancak Feature.xml paketi oluşturulduğunda oluşturulur. Bu dosyalar hakkında daha fazla bilgi için [bkz. SharePoint proje ve proje öğesi şablonları.](../sharepoint/sharepoint-project-and-project-item-templates.md)

## <a name="debug-workflows"></a>İş akışları hata ayıklama
 İş akışı projelerinde hata ayıklarken, iş akışı şablonunu (türüne bağlı [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] olarak) bir kitapca veya listeye ekler. Ardından iş akışı şablonunu el ile veya öğe ekleyerek veya güncelleştirerek başlatabilirsiniz. Daha sonra iş [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] akışında hata ayıklamak için kullanabilirsiniz.

> [!NOTE]
> Diğer derlemelere başvurular eklersanız, bu derlemelerin genel derleme önbelleğine ( ) yüklü olduğundan emin [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] olun. Aksi takdirde iş akışı çözümü başarısız olur. Derlemeleri yükleme hakkında bilgi için bkz. [Bir belge veya öğe üzerinde el ile iş akışı başlatma.](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)

 Ancak, dağıtım işlemi iş akışını başlatmaz. İş akışını web sitesinden SharePoint gerekir. İş akışını word 2010 gibi bir istemci Microsoft Office veya ayrı sunucu tarafı kodu kullanarak da başlatabilirsiniz. SharePoint **Özelleştirme Sihirbazı'nda belirtilen yaklaşımlardan birini kullanın.**

 Örneğin, iş akışının el ile başlatılabilir olduğunu belirttiyebilirsiniz, iş akışını doğrudan kitaplık veya liste öğesinden başlatın. Bir iş akışını el ile başlatma hakkında daha fazla bilgi için bkz. Bir belge [öğesi üzerinde iş akışını el ile başlatma.](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)

## <a name="debug-feature-event-receivers"></a>Hata ayıklama özelliği olay alıcıları
 Varsayılan olarak, bir uygulama SharePoint, bu uygulamanın özellikleri otomatik olarak SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] etkinleştirilir. Ancak, bir özellik tarafından etkinleştirildiğinde hata ayıklayıcısından farklı bir işlemde çalıştırılacı olduğundan, özellik olay alıcılarında hata ayıklarken [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sorunlara neden olur. Bu, kesme noktaları gibi bazı hata ayıklama işlevlerinin düzgün çalışmay anlamına gelir.

 SharePoint'da özelliğin otomatik olarak etkinleştirilmesini devre dışı bırakmak ve Özellik Olay Alıcıları'nın düzgün hata ayıklamasına izin vermek için, hata ayıklamadan önce projenin **Etkin** Dağıtım Yapılandırması **özelliğinin** değerini Etkinleştirme Yok olarak ayarlayın. Ardından, uygulamasındaki uygulamanıza hata ayıklamaya [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint, özelliği uygulamasında el ile SharePoint. Özelliği etkinleştirmek için, SharePoint'de **Site** Eylemleri menüsünü açın, **Site Ayarlar'ı** seçin, **Site** Özelliklerini Yönet  bağlantısını seçin ve ardından normal hata ayıklamaya devam etmek için özelliğin yanındaki Etkinleştir düğmesini seçin.

## <a name="enable-enhanced-debugging-information"></a>Gelişmiş hata ayıklama bilgilerini etkinleştirme
 İşlem (devenv.exe), SharePoint konak işlemi (vssphost4.exe), SharePoint ve WCF katmanı arasındaki karmaşık etkileşimler nedeniyle, oluşturma, dağıtma vb. sırasında oluşan hataları tanılamak zor [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] olabilir.** Bu tür hataları çözmenize yardımcı olmak için gelişmiş hata ayıklama bilgilerini etkinleştirebilirsiniz. Bunu yapmak için, kayıt defterinde aşağıdaki kayıt defteri Windows gidin:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 "EnableDiagnostics" **REG_DWORD** zaten yoksa, el ile oluşturun. "EnableDiagnostics" değerini "1" olarak ayarlayın.

 Bu anahtar değerini 1 olarak ayarlarsanız,  içinde çalışırken proje sistemi hataları oluştuğunda Çıkış penceresinde yığın izleme bilgileri [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] görünür. Gelişmiş hata ayıklama bilgilerini devre dışı bırakmak için EnableDiagnostics değerini 0 olarak ayarlayın veya değeri silin.

 Diğer kayıt defteri anahtarları SharePoint daha fazla bilgi için bkz. SharePoint'deki [Visual Studio.](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Sorun SharePoint giderme](../sharepoint/troubleshooting-sharepoint-solutions.md)

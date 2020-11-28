---
title: SharePoint çözümlerini paketleme ve dağıtma | Microsoft Docs
description: Bir çözüm paketi (. wsp) dosyası kullanarak bir SharePoint sunucusuna dağıtılan SharePoint çözümlerini paketleme ve dağıtma.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd06a5be3c9e7ceea38bdb4560f8b6262175bd45
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305076"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>SharePoint çözümlerini paketleme ve dağıtma
  Genellikle, bir SharePoint çözümü bir SharePoint sunucusuna bir çözüm paketi (. wsp) dosyası kullanılarak dağıtılır. SharePoint proje öğelerinizi Özellikler halinde organize etmek ve SharePoint özelliklerinizi dağıtmak üzere bir paket oluşturmak için Visual Studio 'Yu kullanabilirsiniz.

 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:

- [Özellik ve paket oluşturma](#create-features-and-packages)

- [Özellik ve paketleme aracı desteği](#feature-and-packaging-tool-support)

- [SharePoint çözümlerini dağıtma](#deploy-sharepoint-solutions)

- [SharePoint Çözümlerinde dosya dağıtma](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Özellik ve paket oluşturma
 İlgili SharePoint öğelerini bir *özellik* halinde gruplamak Için Visual Studio 'yu kullanabilirsiniz. Örneğin, bir kişiler liste tanımına yönelik bir özellik liste örneğini ve liste tanımını içerebilir. Bu iki öğeyi, dağıtım amacıyla tek bir özellikte birleştirebilirsiniz. Özellikler hakkında daha fazla bilgi için bkz. [Yapı bloğu: Özellikler](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 Daha sonra, birden çok özelliği, site tanımlarını, derlemeleri ve diğer dosyaları tek bir pakete dağıtmak için bir SharePoint çözüm paketi (*. wsp*) oluşturabilirsiniz. Bu, dosyaları sunucuya dağıtmak üzere SharePoint 'in gerektirdiği bir biçimde depolar. Daha fazla bilgi için bkz. [Yapı bloğu: çözümler](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Özellik ve paketleme aracı desteği
 Daha kolay dağıtım için SharePoint dosyalarınızı Özellikler ve çözüm paketleri halinde hızlıca düzenlemek üzere Visual Studio 'da SharePoint geliştirme araçları 'nı kullanabilirsiniz. Özelliği ve çözüm paketini yapılandırmak için aşağıdaki araçları kullanabilirsiniz.

- Özellik Tasarımcısı ve paket Tasarımcısı.

- Paketleme Gezgini, bir araç penceresidir.

- Çözüm Gezgini.

### <a name="feature-designer-and-package-designer"></a>Özellik Tasarımcısı ve paket Tasarımcısı
 Özellik tasarımcısını kullanarak Özellikler oluşturabilir, kapsamları ayarlayabilir ve diğer özellikleri bağımlılıklar olarak işaretleyebilirsiniz. Tasarımcı Ayrıca her bir özelliği açıklayan son XML dosyasını da görüntüler. Daha fazla bilgi için bkz. [SharePoint özellikleri oluşturma](../sharepoint/creating-sharepoint-features.md).

 Özellik tasarımcısında *kapsamını* ayarlayarak, özelliği belirli bir Web sitesine veya Web siteleri grubuna uygulayın. Tek bir Web sitesi için bir özellik etkinleştirilirse, özellik yalnızca söz konusu web sitesinde çalışmaktadır. Bir site koleksiyonu için bir özellik etkinleştirilirse, özelliğindeki öğeler tüm site koleksiyonu için geçerlidir. Daha fazla bilgi için bkz. [öğe kapsamı](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Özelliği diğer özellikleri kullanıyorsa, özelliğinizi kullanabilmeniz için bağımlı özellikleri işaretlemek üzere bir *özellik etkinleştirme bağımlılığı* ayarlayabilirsiniz. Özellik etkinleştirme bağımlılığı, bağımlı özelliklerin o kapsamda zaten etkin olup olmadığını denetler. Daha fazla bilgi için bkz. [etkinleştirme bağımlılıkları ve kapsamı](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 Paket tasarımcısında, SharePoint öğelerini tek bir çözüm paketine gruplandırabilir ve dağıtım sırasında Web sunucusunun sıfırlanıp sıfırlanmayacağını yapılandırabilirsiniz. Dağıtım sunucusu türünü ayarlamak için **Özellikler** penceresini kullanın. Tasarımcı Ayrıca paket içeriğini açıklayan XML dosyasını da oluşturur. Daha fazla bilgi için bkz. [SharePoint çözüm paketleri oluşturma](../sharepoint/creating-sharepoint-solution-packages.md).

 Dağıtım sırasında, Internet Information Services (IIS) hizmeti, çözüm dosyalarını SharePoint sunucusuna kopyalamak için durdurulur. Visual Studio 'da paket tasarımcısını kullanarak, Web sunucusunun yeniden başlatılması gerekip gerekmediğini belirleyebilirsiniz. Çözümün bir ön uç Web sunucusuna veya bir uygulama sunucusuna dağıtılıp dağıtılmadığını yapılandırmak için **Özellikler** penceresini kullanın. Daha fazla bilgi için bkz. [çözüm öğesi (çözüm)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Paketleme Gezgini
 Özellik tasarımcısını ve paket tasarımcısını tamamlamak için paketleme Gezgini 'ni kullanarak SharePoint dosyalarınızı Özellikler ve paketler halinde gruplandırabilirsiniz. Ayrıca, paketin, özelliklerin, SharePoint proje öğelerinin ve dosyaların hiyerarşik görünümünü görebilirsiniz. Paketleme Gezgini, aşağıdaki görevleri gerçekleştirmek için kullanabileceğiniz bir araç penceresidir:

- SharePoint proje öğelerini ve dosyalarını açın.

- SharePoint proje öğelerini bir özellikten diğerine sürükleyip bırakın.

- SharePoint proje öğelerini ve özelliklerini bir paketten diğerine sürükleyip bırakın.

- Pakete yeni bir özellik ekleyin.

- Bir özellik veya paket Tasarımcısı açın.

- Özellikleri ve paketleri doğrulayın.

  Visual Studio 'daki SharePoint geliştirme araçları, çözüm paketinin doğru biçimlendirildiğinden emin olmak için doğrulama kurallarına sahiptir. Ayrıca, kurallar *. wsp* çözüm dosyasının bir SharePoint sunucusunda başarıyla dağıtılıp etkinleştiribildiğini doğrular. Özelliklerle ilgili XML şeması hakkında daha fazla bilgi için bkz. [özellik şemaları](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  Özel özellik ve paket doğrulama kurallarını SharePoint proje sistemine ekleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: SharePoint çözümleri için özel özellik ve paket doğrulama kuralları oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Paketleme Gezgini hakkında daha fazla bilgi için bkz. [nasıl yapılır: paketleme Gezgini 'ni kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Çözüm Gezgini
 SharePoint projesinin dosyalarını açmak ve açmak için Çözüm Gezgini kullanabilirsiniz. Özellikler, özellik Olay alıcıları ve özellik kaynakları eklemek için Çözüm Gezgini bağlam menüsünü kullanın. Ayrıca, dağıtım için özellikleri ve paketleri yapılandırmak üzere özellik tasarımcıları ve paket tasarımcıları ' nı açabilirsiniz.

## <a name="deploy-sharepoint-solutions"></a>SharePoint çözümlerini dağıtma
 Visual Studio 'da özellikleri ve paketi özelleştirdikten sonra, SharePoint sunucularına dağıtmak üzere bir *. wsp* dosyası oluşturabilirsiniz. Hatalarını ayıklamak ve test etmek için Visual Studio 'Yu kullanabilirsiniz. *wsp* yalnızca geliştirme bilgisayarındaki SharePoint sunucusunda yer alır. SharePoint çözümlerinizi uzak bir SharePoint sunucusuna dağıtma hakkında daha fazla bilgi için bkz. [çözüm dağıtma](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 Geliştirme bilgisayarındaki dağıtım adımlarını da özelleştirebilirsiniz. Daha fazla bilgi için bkz. [SharePoint çözüm paketlerini dağıtma, yayımlama ve yükseltme](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>SharePoint Çözümlerinde dosya dağıtma
 Genellikle, SharePoint çözümünüze bir SharePoint proje öğesi eklediğinizde, gerekli tüm dosyalar dahil edilir. Derlenebilecek dosyalar (kod dosyaları) çözümün çıktı derlemesine yerleşik olarak bulunur. Ancak, örneğin, *. xml*, *. txt* veya kaynak dosyaları gibi derlenebilir olmayan dosyaları bir SharePoint projesine eklemeniz de gerekebilir. Bu dosyalar çözümünüzde otomatik olarak paketlenemez. Paketlendiklerinden emin olmak için, dosyaları eşlenmiş bir klasöre veya SharePoint proje öğesine ekleyin.

 Eşlenmiş klasörlere eklenen dosyalar, çözüm dağıtıldığında otomatik olarak SharePoint Hive 'e kopyalanır. Bir SharePoint proje öğesine eklenen dosyalar, dağıtım **türü** özelliğine göre kısmen ayarlanan her dosya Için **dağıtım konumu** özelliğinde belirtilen konuma dağıtılır. Varsayılan olarak, **dağıtım türü** Özellik değeri **NoDeployment** olur, bu da dosyanın çözümle birlikte dağıtılmadığı anlamına gelir. Özelliği paketini pakete dahil etmek için başka bir değer ayarlamanız gerekir.

 Örneğin, bir SharePoint projesine bir *. xml* dosyası eklemek için şu eylemlerden birini gerçekleştirin:

- Projenize bir SharePoint "düzenleri" eşlenmiş klasör ekleyin. Bu, proje için alt klasörü olan **düzenler** adlı bir klasör **Çözüm Gezgini** oluşturur. *. Xml* dosyasını yeni alt klasöre ekleyin. Varsayılan olarak, dosya altında SharePoint dosya sistemine dağıtılır *. \TEMPLATE\DÜZENLERI \\ \<Folder Name>*. Eşlenmiş klasörler ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: eşlenmiş klasör ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- *. Xml* dosyasını bir SharePoint proje öğesinin klasörüne ekleyin ve ardından *. xml* dosyasının **dağıtım türü** özelliğini **NoDeployment** iken **RootFile** veya **ElementFile** gibi başka bir ayara değiştirin. Uygun **dağıtım türü** ayarı dosya ve projeye bağlıdır. **Dağıtım türü** özelliği ayarları hakkında daha fazla bilgi için bkz. [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md).

  Eklenen bir dosya çözümdeki belirli bir proje için uygulanmayabilir, çözümünüze boş bir SharePoint projesi ekleyebilir ve ardından ek dosyaları ekleyebilirsiniz. SharePoint 'e, özellikle de içerik veritabanına dosya dağıtmaya yönelik başka bir alternatif, projeye bir modül eklemek ve ardından dosyaları modüle eklemektir. Daha fazla bilgi için bkz. [çözümdeki dosyaları dahil etmek için modülleri kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint çözümlerini derleme ve hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)

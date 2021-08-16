---
title: SharePoint Çözüm Paketleri | Microsoft Docs
description: Paket Tasarımcısı'SharePoint dağıtım paketleri oluşturun ve özelleştirin. Paketleme araçlarını, tasarımcı seçeneklerini ve klasör yapısını keşfedin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: f89bb6344ce7be130f0dc4e7d430327cc139175fa4298539855d5b37ec65f01c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425550"
---
# <a name="create-sharepoint-solution-packages"></a>Çözüm SharePoint paketleri oluşturma
  Paket Tasarımcısı'nda dağıtım paketleri oluşturabilir ve özelleştirebilirsiniz. Örneğin, proje öğeleri SharePoint Özellikler ekleyebilir, IIS sunucusunu sıfırlayabilirsiniz, Özellik etkinleştirme kapsamlarını ayarlayabilirsiniz ve Özellik bağımlılıklarını tanımlayabilirsiniz. Tasarımcı ayrıca her paketi açıklayan bir XML dosyası olan bir bildirim de üretir.

## <a name="packaging-tools"></a>Paketleme araçları
 Paketi özelleştirmek ve **bildirimi oluşturmak** için Paket Tasarımcısı'nın kullanabilirsiniz. Proje öğelerini SharePoint, Web sunucusunun sıfırlanacak olup olmadığını yapılandırıp dağıtım sunucusu türünü ayarlayabilirsiniz. Daha fazla bilgi için, [bkz. How to: Add and remove features and items to a package by using the Package Designer](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Alternatif olarak, Paketleme Gezgini'ni **kullanarak** paket dosyanız *(.wsp)* özellikleri ve öğeleri değiştirebilirsiniz. Daha fazla bilgi için [bkz. Paketleme Gezgini'ni](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)kullanarak Pakete özellik ve öğe ekleme ve kaldırma.

 Visual Studio MSBuild dağıtmak üzere paket (*.wsp*) dosyaları oluşturmak için SharePoint kullanabilirsiniz. Bu işlem, dağıtım için gereken bildirim SharePoint üretir. Daha fazla bilgi için, [bkz. How to: Create a SharePoint Solution Package by using MSBuild görevleri](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Paket tasarımcısı seçenekleri
 Aşağıdaki tabloda, Paket Tasarımcısı ile SharePoint özelleştirebileceğiniz **özellikler yer alır.**

|Paket Tasarımcısı Özelliği|Varsayılan ayarın açıklaması|
|-------------------------------|------------------------------------|
|Name|Gereklidir. Paketin varsayılan adı *ProjectName olarak ayarlanır.*|
|WebServer'ı Sıfırlama|İsteğe bağlı. Web sunucusuna *.wsp* dosyası yüklendikten sonra Web sunucusunu yeniden başlatmak SharePoint seçin.|
|Dağıtım Sunucusu Türü|İsteğe bağlı. Paketi barındıran sunucunun türünü temsil eder. Ayarlanmazsa, bu varsayılan olarak WebFrontEnd olur.<br /><br /> ApplicationServer: Hizmetleri barındıran bir sunucuyu açıklar.<br /><br /> WebFrontEnd: Web sitelerini barındıran bir sunucuyu açıklar.|
|Çözümdeki Öğeler|Tüm SharePoint proje öğeleri ve pakete eklen all.|
|Paket öğeleri|İsteğe bağlı. Tüm SharePoint paketinize dağıtmak istediğiniz tüm öğeleri ve Özellikleri içerir.|

## <a name="configure-the-packaging-process"></a>Paketleme işlemini yapılandırma
 Bu SharePoint çözümlerini Visual Studio, projelerin nasıl paketlen olduğunu özelleştirebilirsiniz.

 Aşağıdaki tabloda, *.wsp* MSBuild özelleştirmek için kullanabileceğiniz iki farklı hedef yer almaktadır.

|Hedef|Açıklama|
|------------|-----------------|
|BeforeLayout|Dosyalar bir ara dizine kopyalanmadan hemen önce görevleri gerçekleştiren hedef. Bir paket dosyası ( .wsp ) oluşturmadan önce *dosyaları değiştirebilirsiniz.*|
|AfterLayout|Dosyalar bir ara dizine kopyalandıktan hemen sonra görevleri gerçekleştiren hedef.|

 Daha fazla bilgi [için, Nasıl: SharePoint Hedeflerini](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)kullanarak bir MSBuild paketi özelleştirme.

## <a name="packaging-architecture"></a>Paketleme mimarisi
 Aşağıdaki adımlar, uygulama içinde bir SharePoint paketi (*.wsp*) Visual Studio.

1. Özellikler ve paketler, paketin fiziksel ve semantik yapısının doğru olduğundan emin olmak için doğrulanır.

2. Pakette yer alan Özellikler, proje öğeleri ve paket dosyaları numaralandı. Paketlere ve Özelliklere ilişkin bildirim dosyaları, dağıtım ve etkinleştirme için gerekli tüm bilgileri içerecek şekilde dönüştürülmektedir. Belirteçler, tam değerle değiştirilir.

3. Özelleştirilebilir BeforeLayout MSBuild hedef gerçekleştirilir. *.wsp* dosyası oluşturulmadan önce pakette özel değişiklikler yapmak için bu adımı oluşturabilirsiniz.

4. Numaralanan dosyalar bir ara dizine kopyalanır.

5. Özelleştirilebilir AfterLayout MSBuild hedef gerçekleştirilir. *.wsp* dosyası oluşturulmadan önce pakette özel değişiklikler yapmak için bu adımı oluşturabilirsiniz.

6. Ara dizinde yer alan dosyalar *.wsp dosyasına* eklenir.

## <a name="package-folder-structure"></a>Paket klasörü yapısı
 Uygulama projenizi SharePoint, *SolutionFolder\bin \\ \<BuildConfiguration>* klasöründe sizin için bir *.wsp* dosyası oluşturulur. Örneğin, çözümünüz *C:\Visual Studio 2013\Projects\ListDefinition1* konumunda ve derleme yapılandırmanız Yayın olarak *ayarlanmışsa, .wsp* dosyası *C:\Visual Studio 2013\Projects\ListDefinition1\bin\Release* konumunda bulunur.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl SharePoint: SharePoint paketi özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl kullanılır: Paket Tasarımcısını kullanarak pakete özellik ve öğe ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Nasıl SharePoint: SharePoint görevleri kullanarak MSBuild oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Nasıl SharePoint: SharePoint görevleri kullanarak MSBuild oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Nasıl SharePoint: SharePoint hedeflerini kullanarak MSBuild özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)

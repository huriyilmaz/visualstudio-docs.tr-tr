---
title: SharePoint çözüm paketleri oluşturma | Microsoft Docs
description: paket tasarımcısını kullanarak SharePoint çözümleri için dağıtım paketleri oluşturun ve özelleştirin. Paketleme araçları, tasarımcı seçenekleri ve klasör yapısını gezin.
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
ms.openlocfilehash: d395dcbc0c1600209d6e1bd04b4c88059b9cf60e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635654"
---
# <a name="create-sharepoint-solution-packages"></a>SharePoint çözüm paketleri oluşturma
  Paket Tasarımcısını kullanarak dağıtım paketleri oluşturabilir ve bunları özelleştirebilirsiniz. örneğin, SharePoint proje öğeleri ve özellikler ekleyebilir, ııs sunucusunu sıfırlayabilir, özellik etkinleştirme kapsamlarını ayarlayabilir ve özellik bağımlılıklarını belirleyebilirsiniz. Tasarımcı Ayrıca her paketi açıklayan bir XML dosyası bildirimi de oluşturur.

## <a name="packaging-tools"></a>Paketleme araçları
 Paketi özelleştirmek ve bildirimi oluşturmak için **Paket Tasarımcısını** kullanabilirsiniz. SharePoint proje öğelerini dahil edebilir, Web sunucusunun sıfırlanması gerekip gerekmediğini yapılandırabilir ve dağıtım sunucusu türünü ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Alternatif olarak, paket dosyanızdaki (*. wsp*) özellikleri ve öğeleri değiştirmek Için **paketleme Gezginini** kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: paketleme Gezgini 'ni kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 SharePoint çözümünüzü dağıtmak üzere paket (*. wsp*) dosyaları oluşturmak için Visual Studio ve MSBuild kullanabilirsiniz. bu işlem, SharePoint dağıtımı için gereken bildirim dosyalarını oluşturur. daha fazla bilgi için, bkz. [nasıl yapılır: MSBuild görevleri kullanarak SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Paket Tasarımcısı seçenekleri
 aşağıdaki tabloda, **paket tasarımcısı** ile SharePoint paketlerinde özelleştirebileceğiniz özellikler gösterilmektedir.

|Paket Tasarımcısı özelliği|Varsayılan ayarın açıklaması|
|-------------------------------|------------------------------------|
|Name|Gereklidir. Paketin varsayılan adı *ProjectName* olarak ayarlanır.|
|Web sunucusu sıfırlama|İsteğe bağlı. *. wsp* dosyası SharePoint sunucusuna yüklendikten sonra Web sunucusunu yeniden başlatmak istiyorsanız seçin.|
|Dağıtım sunucusu türü|İsteğe bağlı. Paketi barındıran sunucunun türünü temsil eder. Ayarlanmamışsa, varsayılan olarak Webön uç olur.<br /><br /> ApplicationServer: hizmetleri barındıran bir sunucuyu tanımlar.<br /><br /> Webön uç: Web sitelerini barındıran bir sunucuyu tanımlar.|
|Çözümdeki öğeler|tüm SharePoint proje öğeleri ve pakete eklenebilecek özellikler.|
|Paketteki öğeler|İsteğe bağlı. paketinize dağıtmak istediğiniz tüm öğeleri ve özellikleri SharePoint.|

## <a name="configure-the-packaging-process"></a>Paketleme işlemini yapılandırma
 Visual Studio SharePoint çözümleri geliştirip, projelerin paketlenebilme şeklini özelleştirebilirsiniz.

 aşağıdaki tabloda, *. wsp* dosyasının nasıl oluşturulduğunu özelleştirmek için kullanabileceğiniz iki MSBuild hedefi gösterilmektedir.

|Hedef|Description|
|------------|-----------------|
|BeforeLayout|Dosyalar bir ara dizine kopyalanmadan hemen önce görevleri gerçekleştiren hedef. Dosyaları bir paket dosyası (*. wsp*) oluşturmadan önce değiştirebilirsiniz.|
|AfterLayout|Dosyalar bir ara dizine kopyalandıktan hemen sonra görevleri gerçekleştiren hedef.|

 daha fazla bilgi için [nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Paketleme mimarisi
 Visual Studio ' de bir SharePoint paketi (*. wsp*) oluşturduğunuzda aşağıdaki adımlar oluşur.

1. Özellikler ve paketler, paketin fiziksel ve anlam yapısının doğru olduğundan emin olmak için onaylanır.

2. Paketteki özellikler, proje öğeleri ve paket dosyaları numaralandırılır. Paketler ve özellikler için bildirim dosyaları, dağıtım ve etkinleştirmeye yönelik tüm gerekli bilgileri içerecek şekilde dönüştürülür. Belirteçler tam nitelikli değerle değiştirilmiştir.

3. özelleştirilebilir BeforeLayout MSBuild hedefi gerçekleştirilir. Bu adımı, *. wsp* dosyası oluşturulmadan önce pakette herhangi bir özel değişiklik yapmak için oluşturabilirsiniz.

4. Numaralandırılmış dosyalar bir ara dizine kopyalanır.

5. özelleştirilebilir afterlayout MSBuild hedefi gerçekleştirilir. Bu adımı, *. wsp* dosyası oluşturulmadan önce pakette herhangi bir özel değişiklik yapmak için oluşturabilirsiniz.

6. Ara dizindeki dosyalar *. wsp* dosyasına eklenir.

## <a name="package-folder-structure"></a>Paket klasörü yapısı
 SharePoint projenizi paketlemeyi yaparken, *solutionfolder\bin \\ \<BuildConfiguration>* klasöründe sizin için bir *. wsp* dosyası oluşturulur. örneğin, çözümünüz *c:\ Visual Studio 2013 \projelerlistdefinition1* ' de ise ve derleme yapılandırmanız yayın olarak ayarlandıysa, *. wsp* dosyası *c:\ Visual Studio 2013 \projelerilistdefinition1\bin\release* konumunda bulunur.

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [nasıl yapılır: MSBuild görevleri kullanarak SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [nasıl yapılır: MSBuild görevleri kullanarak SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)

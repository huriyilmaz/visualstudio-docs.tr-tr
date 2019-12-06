---
title: SharePoint çözüm paketleri oluşturuluyor | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b250be3b61cdfc524f049f952f0cf7e65f1c295a
ms.sourcegitcommit: 174c992ecdc868ecbf7d3cee654bbc2855aeb67d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74876070"
---
# <a name="create-sharepoint-solution-packages"></a>SharePoint çözüm paketleri oluşturma
  Paket Tasarımcısını kullanarak dağıtım paketleri oluşturabilir ve bunları özelleştirebilirsiniz. Örneğin, SharePoint proje öğeleri ve özellikleri ekleyebilir, IIS sunucusunu sıfırlayabilir, özellik etkinleştirme kapsamlarını ayarlayabilir ve özellik bağımlılıklarını belirleyebilirsiniz. Tasarımcı Ayrıca her paketi açıklayan bir XML dosyası bildirimi de oluşturur.

## <a name="packaging-tools"></a>Paketleme araçları
 Paketi özelleştirmek ve bildirimi oluşturmak için **Paket Tasarımcısını** kullanabilirsiniz. SharePoint proje öğelerini dahil edebilir, Web sunucusunun sıfırlanması gerekip gerekmediğini yapılandırabilir ve dağıtım sunucusu türünü ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Alternatif olarak, paket dosyanızdaki ( *. wsp*) özellikleri ve öğeleri değiştirmek Için **paketleme Gezginini** kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: paketleme Gezgini 'ni kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 SharePoint Çözümünüzü dağıtmak üzere Package ( *. wsp*) dosyalarını oluşturmak Için Visual Studio ve MSBuild kullanabilirsiniz. Bu işlem, SharePoint dağıtımı için gereken bildirim dosyalarını oluşturur. Daha fazla bilgi için bkz. [nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Paket Tasarımcısı seçenekleri
 Aşağıdaki tabloda, SharePoint paketlerinde **paket Tasarımcısı**ile özelleştirebileceğiniz özellikler gösterilmektedir.

|Paket Tasarımcısı özelliği|Varsayılan ayarın açıklaması|
|-------------------------------|------------------------------------|
|Name|Gerekli. Paketin varsayılan adı *ProjectName*olarak ayarlanır.|
|Web sunucusu sıfırlama|İsteğe bağlı. *. Wsp* dosyası SharePoint sunucusuna yüklendikten sonra Web sunucusunu yeniden başlatmak istiyorsanız seçin.|
|Dağıtım sunucusu türü|İsteğe bağlı. Paketi barındıran sunucunun türünü temsil eder. Ayarlanmamışsa, varsayılan olarak Webön uç olur.<br /><br /> ApplicationServer: hizmetleri barındıran bir sunucuyu tanımlar.<br /><br /> Webön uç: Web sitelerini barındıran bir sunucuyu tanımlar.|
|Çözümdeki öğeler|Pakete eklenebilecek tüm SharePoint proje öğeleri ve özellikleri.|
|Paketteki öğeler|İsteğe bağlı. Paketinize dağıtmak istediğiniz tüm SharePoint öğeleri ve özellikleri.|

## <a name="configure-the-packaging-process"></a>Paketleme işlemini yapılandırma
 Visual Studio 'da SharePoint çözümleri geliştirip, projelerin paketlenebilme şeklini özelleştirebilirsiniz.

 Aşağıdaki tabloda, *. wsp* dosyasının nasıl oluşturulduğunu özelleştirmek için kullanabileceğiniz iki MSBuild hedefi gösterilmektedir.

|Hedef|Açıklama|
|------------|-----------------|
|BeforeLayout|Dosyalar bir ara dizine kopyalanmadan hemen önce görevleri gerçekleştiren hedef. Dosyaları bir paket dosyası ( *. wsp*) oluşturmadan önce değiştirebilirsiniz.|
|AfterLayout|Dosyalar bir ara dizine kopyalandıktan hemen sonra görevleri gerçekleştiren hedef.|

 Daha fazla bilgi için [nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Paketleme mimarisi
 Visual Studio 'da bir SharePoint paketi ( *. wsp*) oluşturduğunuzda aşağıdaki adımlar oluşur.

1. Özellikler ve paketler, paketin fiziksel ve anlam yapısının doğru olduğundan emin olmak için onaylanır.

2. Paketteki özellikler, proje öğeleri ve paket dosyaları numaralandırılır. Paketler ve özellikler için bildirim dosyaları, dağıtım ve etkinleştirmeye yönelik tüm gerekli bilgileri içerecek şekilde dönüştürülür. Belirteçler tam nitelikli değerle değiştirilmiştir.

3. Özelleştirilebilir BeforeLayout MSBuild hedefi gerçekleştirilir. Bu adımı, *. wsp* dosyası oluşturulmadan önce pakette herhangi bir özel değişiklik yapmak için oluşturabilirsiniz.

4. Numaralandırılmış dosyalar bir ara dizine kopyalanır.

5. Özelleştirilebilir AfterLayout MSBuild hedefi gerçekleştirilir. Bu adımı, *. wsp* dosyası oluşturulmadan önce pakette herhangi bir özel değişiklik yapmak için oluşturabilirsiniz.

6. Ara dizindeki dosyalar *. wsp* dosyasına eklenir.

## <a name="package-folder-structure"></a>Paket klasörü yapısı
 SharePoint projenizi paketlemeyi yaparken, *Solutionfolder\bin\\\<BuildConfiguration >* klasöründe sizin için bir *. wsp* dosyası oluşturulur. Örneğin, çözümünüz *C:\Visual Studio 2013 \ Projelerilistdefinition1* ' de ise ve derleme yapılandırmanız Release olarak ayarlandıysa, *. wsp* dosyası *c:\Visual Studio 2013 \ Projeler\listdefinition1\bin\release*konumunda bulunur.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: bir SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Nasıl yapılır: Paket Tasarımcısını kullanarak bir pakete Özellikler ve öğeler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Nasıl yapılır: MSBuild hedeflerini kullanarak SharePoint çözüm paketini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)

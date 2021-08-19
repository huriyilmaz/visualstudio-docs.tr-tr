---
title: Çözümdeki dosyaları dahil etmek için modülleri kullanma | Microsoft Docs
description: dosya türleri (örneğin, ana sayfalar) ne olursa olsun SharePoint sunucusuna dosya dağıtmak için bir SharePoint çözümündeki dosyalar için modüller veya kapsayıcılar kullanın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 11707021ab8cd3275980dfce24baf24facdb03e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115505"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Çözümdeki dosyaları dahil etmek için modülleri kullanma
  dosya türleri ne olursa olsun, yeni ana sayfalar gibi SharePoint sunucusuna dosya dağıtmak isteyebileceğiniz zamanlar olabilir. Bunu yapmak için *modüller* ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] kod modülleriyle karıştırılmamalıdır) kullanabilirsiniz. modüller SharePoint çözümdeki dosyalar için kapsayıcılardır. çözüm dağıtıldığında, modüldeki dosyalar SharePoint sunucusundaki belirtilen klasörlere kopyalanır.

## <a name="module-items-and-elements"></a>Modül öğeleri ve öğeleri
 Bir modül oluşturmak için bunu **Yeni öğe Ekle** iletişim kutusunda seçerek bir projeye ekleyin. daha sonra, *Elements.xml* dosyasını, dağıtmak istediğiniz dosyaların adlarını içerecek şekilde değiştirin, burada sistemde bulunur ve SharePoint sunucusunda nereye kopyalanmaları gerekir.

 Modül için *Elements.xml* dosyasına bir örnek aşağıda verilmiştir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Yeni oluşturulan modüller aşağıdaki varsayılan dosyaları içerir:

|Dosya Adı|Açıklama|
|---------------|-----------------|
|*Elements.xml*|Modülün tanım dosyası.|
|*Sample.txt*|Modüldeki bir dosyaya örnek olarak hizmet veren bir yer tutucu dosyası.|

 *Elements.xml* dosyası aşağıdaki öğeleri içerir:

|Öğe Adı|Açıklama|
|------------------|-----------------|
|Öğeler|Modülde tanımlanan tüm öğeleri içerir.|
|Modül|Module öğesi, ' ın ' de modül adını belirten tek bir özniteliğe ( *Name*) sahiptir `<Module Name="Module1">` .<br /><br /> Modülün adını (veya *klasör adı* özelliğini) değiştirirseniz, bu adı modül öğesinde el ile güncelleştirmeniz gerektiğini unutmayın.<br /><br /> modül öğesinde dosya (ler) için bir alt dizin belirtirseniz, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) bunlar için otomatik olarak eşleşen bir dizin yapısı oluşturulur.|
|Dosya|Dosya öğesinin iki parametresi, *yolu* ve *URL 'si* vardır.<br /><br /> -Path: SharePoint çözümündeki dosyanın adı ve konumu. Biçimi, `Path="Module1\Sample.txt"` .<br /><br /> -Url: dosyanın SharePoint sunucuda dağıtılacağı konum. Biçimi, `Url="Module1/Sample.txt"` .<br /><br /> -Type: iki ayarı olan isteğe bağlı bir öznitelik: *GhostableInLibrary* ve *Ghostable*. Biçimi, `Type="GhostableInLibrary"` . *GhostableInLibrary* belirtme, dosyanın kitaplığa eklendiğinde dosyayı eşlik edecek bir liste öğesiyle birlikte SharePoint bir belge kitaplığına eklenebileceği anlamına gelir. *Ghostable* belirtme, dosyanın belge kitaplığı dışına SharePoint eklenmesine neden olur.|

 Dağıtmak istediğiniz her dosya `<File>` *Elements.xml* içinde ayrı bir öğe girişi gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: modül kullanarak dosyaları Içerme](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Nasıl yapılır: dosya sağlama](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

---
title: Çözümdeki dosyaları dahil etmek için modülleri kullanma | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 778bbc9cff2d7853628edbb5be6466acc55d9ab8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015820"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Çözümdeki dosyaları dahil etmek için modülleri kullanma
  Dosyaları, yeni ana sayfalar gibi dosya türlerine bakılmaksızın SharePoint sunucusuna dağıtmak isteyebileceğiniz zamanlar olabilir. Bunu yapmak için *modüller* ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] kod modülleriyle karıştırılmamalıdır) kullanabilirsiniz. Modüller bir SharePoint çözümündeki dosyalar için kapsayıcılardır. Çözüm dağıtıldığında, modüldeki dosyalar SharePoint sunucusundaki belirtilen klasörlere kopyalanır.

## <a name="module-items-and-elements"></a>Modül öğeleri ve öğeleri
 Bir modül oluşturmak için bunu **Yeni öğe Ekle** iletişim kutusunda seçerek bir projeye ekleyin. Daha sonra, *Elements.xml* dosyasını, dağıtmak istediğiniz dosyaların adlarını, sistemde bulundukları ve SharePoint sunucusunda nereye kopyalanmaları içerecek şekilde değiştirin.

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

|Dosya Adı|Description|
|---------------|-----------------|
|*Elements.xml*|Modülün tanım dosyası.|
|*Sample.txt*|Modüldeki bir dosyaya örnek olarak hizmet veren bir yer tutucu dosyası.|

 *Elements.xml* dosyası aşağıdaki öğeleri içerir:

|Öğe Adı|Description|
|------------------|-----------------|
|Öğeler|Modülde tanımlanan tüm öğeleri içerir.|
|Modül|Module öğesi, ' ın ' de modül adını belirten tek bir özniteliğe ( *Name*) sahiptir `<Module Name="Module1">` .<br /><br /> Modülün adını (veya *klasör adı* özelliğini) değiştirirseniz, bu adı modül öğesinde el ile güncelleştirmeniz gerektiğini unutmayın.<br /><br /> Modül öğesinde dosya (ler) için bir alt dizin belirtirseniz, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) onlar için otomatik olarak eşleşen bir dizin yapısı oluşturur.|
|Dosya|Dosya öğesinin iki parametresi, *yolu* ve *URL 'si*vardır.<br /><br /> -Path: SharePoint çözümündeki dosyanın adı ve konumu. Biçimi, `Path="Module1\Sample.txt"` .<br /><br /> -URL: dosyanın SharePoint sunucusunda dağıtılacağı konum. Biçimi, `Url="Module1/Sample.txt"` .<br /><br /> -Type: iki ayarı olan isteğe bağlı bir öznitelik: *GhostableInLibrary* ve *Ghostable*. Biçimi, `Type="GhostableInLibrary"` . *GhostableInLibrary* belirtme, dosyanın kitaplığa eklendiği sırada dosyaya eşlik eden bir liste öğesiyle birlikte SharePoint 'teki bir belge kitaplığına eklenebileceği anlamına gelir. *Ghostable* belirtme, dosyanın belge kitaplığı dışından SharePoint 'e eklenmesine neden olur.|

 Dağıtmak istediğiniz her dosya `<File>` *Elements.xml*içinde ayrı bir öğe girişi gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: modül kullanarak dosyaları Içerme](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Nasıl yapılır: dosya sağlama](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [SharePoint çözümlerini geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

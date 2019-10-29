---
title: Çözümdeki dosyaları dahil etmek için modülleri kullanma | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 4f8f2aa6c5d86af2424a811b6167829cefdb6fb5
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985303"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Çözümdeki dosyaları dahil etmek için modülleri kullanma
  Dosyaları, yeni ana sayfalar gibi dosya türlerine bakılmaksızın SharePoint sunucusuna dağıtmak isteyebileceğiniz zamanlar olabilir. Bunu yapmak için *modüller* ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] kod modülleriyle karıştırılmamalıdır) kullanabilirsiniz. Modüller bir SharePoint çözümündeki dosyalar için kapsayıcılardır. Çözüm dağıtıldığında, modüldeki dosyalar SharePoint sunucusundaki belirtilen klasörlere kopyalanır.

## <a name="module-items-and-elements"></a>Modül öğeleri ve öğeleri
 Bir modül oluşturmak için bunu **Yeni öğe Ekle** iletişim kutusunda seçerek bir projeye ekleyin. Daha sonra, kendi *Elements. xml* dosyasını, dağıtmak istediğiniz dosyaların adlarını içerecek şekilde değiştirin, burada sistemde bulunur ve SharePoint sunucusuna kopyalanmaları gerekir.

 Modül için *Elements. xml* dosyasına bir örnek aşağıda verilmiştir:

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
|*Elements. xml*|Modülün tanım dosyası.|
|*Sample. txt*|Modüldeki bir dosyaya örnek olarak hizmet veren bir yer tutucu dosyası.|

 *Elements. xml* dosyası aşağıdaki öğeleri içerir:

|Öğe adı|Açıklama|
|------------------|-----------------|
|Öğeler|Modülde tanımlanan tüm öğeleri içerir.|
|Modül|Module öğesi, `<Module Name="Module1">`biçimindeki modülün adını belirten tek bir özniteliğe, *adına*sahiptir.<br /><br /> Modülün adını (veya *klasör adı* özelliğini) değiştirirseniz, bu adı modül öğesinde el ile güncelleştirmeniz gerektiğini unutmayın.<br /><br /> Modül öğesinde dosya (ler) için bir alt dizin belirtirseniz, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) otomatik olarak bu kendileri için eşleşen bir dizin yapısı oluşturur.|
|Dosya|Dosya öğesinin iki parametresi, *yolu* ve *URL 'si*vardır.<br /><br /> -Path: SharePoint çözümündeki dosyanın adı ve konumu. Biçim, `Path="Module1\Sample.txt"`.<br /><br /> -URL: dosyanın SharePoint sunucusunda dağıtılacağı konum. Biçim, `Url="Module1/Sample.txt"`.<br /><br /> -Type: iki ayarı olan isteğe bağlı bir öznitelik: *GhostableInLibrary* ve *Ghostable*. Biçim, `Type="GhostableInLibrary"`. *GhostableInLibrary* belirtme, dosyanın kitaplığa eklendiği sırada dosyaya eşlik eden bir liste öğesiyle birlikte SharePoint 'teki bir belge kitaplığına eklenebileceği anlamına gelir. *Ghostable* belirtme, dosyanın belge kitaplığı dışından SharePoint 'e eklenmesine neden olur.|

 Dağıtmak istediğiniz her dosya *Elements. xml*içinde ayrı bir `<File>` öğe girişi gerektirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: modül kullanarak dosyaları Içerme](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Nasıl yapılır: dosya sağlama](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [SharePoint çözümlerini geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

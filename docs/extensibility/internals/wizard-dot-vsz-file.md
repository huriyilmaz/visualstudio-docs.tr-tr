---
title: Sihirbaz (. Vsz) Dosya | Microsoft Docs
description: IDE'nin sihirbazları başlatmak için kullandığı .vsz dosyaları hakkında bilgi öğrenin. Dosyalar hangi sihirbazın çağrıleceği ve sihirbaza nelerin geçeceği hakkında bilgi içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 716ac3ce08b51695219b5c8cd33f49134f33d3626943e02c939c7427920f6e87
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121261131"
---
# <a name="wizard-vsz-file"></a>Sihirbaz (.Vsz) Dosyası

Tümleşik geliştirme ortamı (IDE), sihirbazları başlatmak için .vsz dosyalarını kullanır. Bu .vsz dosyaları, IDE'nin hangi sihirbazı çağıran ve sihirbaza hangi bilgilerin geçeceği belirlemek için kullandığı bilgileri içerir.

.vsz dosyası, bölüm olmayan .ini biçimlendirilmiş bir metin dosyasının sürümüdür. IDE tarafından bilinen bilgiler dosyanın başında depolanır. Bu, sihirbaz arasında IDE'nin çağıran bir bağlantı ve IDE'ye geçirilen .vsz dosyasındaki parametreleri sağlar. Dosyanın geri kalanı, sihirbaza özgü ve IDE tarafından toplanacak ve belirli bir sihirbaza geçir edilecek parametreleri sağlar.

Aşağıdaki örnek bir .vsz dosyasının içeriğini gösterir.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

.vsz dosyasındaki parçalar aşağıda ve ve ardından ve hatta yer alan bölümlerden oluşur.

|Bölüm|Açıklama|
|----------|-----------------|
|Vswizard|Dosyanın ilk parametresi, şablon dosyası biçiminin sürüm numarasıdır. Bu sürüm numarası 6.0, 7.0, 7.1 veya 8.0 olabilir. Diğer sayılar başlatılamayacak ve Geçersiz Biçim hatasına neden olacak.|
|Sihirbazı|Bu alan, sihirbazın OLE ProgID'sini veya alternatif olarak IDE tarafından ortak olarak oluşturulur sihirbazın CLSID'sini guid dizesi gösterimini içerir.|
|Param|Bu parçalar isteğe bağlıdır. Gereken sayıda ekleyebilir.|

Parametreler, .vsz dosyasının sihirbaza ek özel parametreler iletir. Her değer, sihirbaza değişken dizisinde bir dize öğesi olarak geçirildi. Daha fazla bilgi için [bkz. Özel Parametreler.](../../extensibility/internals/custom-parameters.md)

.vsz dosyanıza varsayılan bir yerel ayar kimliği eklemek için =xxxx'i belirtin; burada xxxx yerel ayar kimliğidir, örneğin İngilizce için `FALLBACK_LCID` 1033. Parametre `FALLBACK_LCID` tanımlandığı zaman, geçerli kimlik bulunamasa sihirbaz sağlanan geri dönüş yerel ayar kimliğini kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

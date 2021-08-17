---
title: Sihirbaz (. Vsz) dosyası | Microsoft Docs
description: IDE 'nin sihirbazları başlatmak için kullandığı. vsz dosyaları hakkında bilgi edinin. Dosyalar, hangi sihirbazın çağrılacağını ve sihirbaza ne geçilecek hakkında bilgiler içerir.
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
ms.openlocfilehash: cf6d381ff163711eb1026071a91660d74d835c71
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041769"
---
# <a name="wizard-vsz-file"></a>Sihirbaz (.Vsz) Dosyası

Tümleşik geliştirme ortamı (IDE), sihirbazları başlatmak için. vsz dosyalarını kullanır. Bu. vsz dosyaları, hangi sihirbazın çağrılacağını ve sihirbaza hangi bilgilerin geçirileceğini belirlemek için IDE 'nin kullandığı bilgileri içerir.

. Vsz dosyası, bölümü olmayan .ini biçimli bir metin dosyasının sürümüdür. IDE tarafından bilinen bilgiler dosyanın başında depolanır. Bu, IDE 'nin çağırdığı sihirbaz ve IDE 'ye geçirilecek. vsz dosyasındaki parametreler arasında bir bağlantı sağlar. Dosyanın geri kalanı sihirbaza özgü ve IDE tarafından toplanacak ve belirli sihirbaza geçirilecek parametreler sağlar.

Aşağıdaki örnek bir. vsz dosyasının içeriğini gösterir.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

. Vsz dosyasındaki parçalar aşağıda verilmiştir.

|Bölüm|Açıklama|
|----------|-----------------|
|VSWizard|Dosyadaki ilk parametre, şablon dosya biçiminin sürüm numarasıdır. Bu sürüm numarası 6,0, 7,0, 7,1 veya 8,0 olmalıdır. Diğer sayılar başlatılamaz ve geçersiz biçim hatasına neden olabilir.|
|Ekleme|Bu alan, sihirbazın OLE ProgID 'sini veya alternatif olarak IDE tarafından birlikte oluşturulan sihirbazın CLSID 'inin GUID dize gösterimini içerir.|
|Param|Bu parçalar isteğe bağlıdır. Gereken kadar çok sayıda ekleyebilirsiniz.|

Parametreler,. vsz dosyasını Sihirbaza ek özel parametreler geçirecek şekilde etkinleştirir. Her değer, sihirbaza bir varyant dizisinde dize öğesi olarak geçirilir. Daha fazla bilgi için bkz. [özel parametreler](../../extensibility/internals/custom-parameters.md).

. Vsz dosyanıza varsayılan bir yerel ayar KIMLIĞI eklemek için, `FALLBACK_LCID` = xxxx belirtin; burada xxxx yerel ayar kimliği, örneğin, İngilizce için 1033. `FALLBACK_LCID`Parametre tanımlandığında, sihirbaz, GEÇERLI kimlik bulunamazsa, sağlanan geri dönüş yerel ayar kimliğini kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

---
title: Sihirbaz (. Vsz) dosyası | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0fedf409c0ca320c054ddf1cc16318d08d25463a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703319"
---
# <a name="wizard-vsz-file"></a>Sihirbaz (.Vsz) Dosyası

Tümleşik geliştirme ortamı (IDE), sihirbazları başlatmak için. vsz dosyalarını kullanır. Bu. vsz dosyaları, hangi sihirbazın çağrılacağını ve sihirbaza hangi bilgilerin geçirileceğini belirlemek için IDE 'nin kullandığı bilgileri içerir.

. Vsz dosyası, bölümü olmayan. ini biçimli bir metin dosyasının sürümüdür. IDE tarafından bilinen bilgiler dosyanın başında depolanır. Bu, IDE 'nin çağırdığı sihirbaz ve IDE 'ye geçirilecek. vsz dosyasındaki parametreler arasında bir bağlantı sağlar. Dosyanın geri kalanı sihirbaza özgü ve IDE tarafından toplanacak ve belirli sihirbaza geçirilecek parametreler sağlar.

Aşağıdaki örnek bir. vsz dosyasının içeriğini gösterir.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

. Vsz dosyasındaki parçalar aşağıda verilmiştir.

|Bölüm|Description|
|----------|-----------------|
|VSWizard|Dosyadaki ilk parametre, şablon dosya biçiminin sürüm numarasıdır. Bu sürüm numarası 6,0, 7,0, 7,1 veya 8,0 olmalıdır. Diğer sayılar başlatılamaz ve geçersiz biçim hatasına neden olabilir.|
|Ekleme|Bu alan, sihirbazın OLE ProgID 'sini veya alternatif olarak IDE tarafından birlikte oluşturulan sihirbazın CLSID 'inin GUID dize gösterimini içerir.|
|Param|Bu parçalar isteğe bağlıdır. Gereken kadar çok sayıda ekleyebilirsiniz.|

Parametreler,. vsz dosyasını Sihirbaza ek özel parametreler geçirecek şekilde etkinleştirir. Her değer, sihirbaza bir varyant dizisinde dize öğesi olarak geçirilir. Daha fazla bilgi için bkz. [özel parametreler](../../extensibility/internals/custom-parameters.md).

. Vsz dosyanıza varsayılan bir yerel ayar KIMLIĞI eklemek için, `FALLBACK_LCID` = xxxx belirtin; burada xxxx yerel ayar kimliği, örneğin, İngilizce için 1033. `FALLBACK_LCID`Parametre tanımlandığında, sihirbaz, GEÇERLI kimlik bulunamazsa, sağlanan geri dönüş yerel ayar kimliğini kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

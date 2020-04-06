---
title: Sihirbaz (. Vsz) Dosya | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703319"
---
# <a name="wizard-vsz-file"></a>Sihirbaz (.Vsz) Dosyası

Tümleşik geliştirme ortamı (IDE), sihirbazları başlatmak için .vsz dosyalarını kullanır. Bu .vsz dosyaları, IDE'nin hangi sihirbazı arayacağını ve sihirbaza hangi bilgileri aktarılabilmek için kullandığı bilgileri içerir.

.vsz dosyası, .ini biçimli ve bölümü olmayan bir metin dosyasının sürümüdür. IDE tarafından bilinen bilgiler dosyanın başında saklanır. Bu, IDE'nin çağırdığı sihirbaz la .vsz dosyasındaki parametreler arasında IDE'ye geçirilecek bir bağlantı sağlar. Dosyanın geri kalanı sihirbaza özgü ve IDE tarafından toplanacak ve belirli sihirbaza geçirilecek parametreler sağlar.

Aşağıdaki örnekte .vsz dosyasının içeriği gösterilmektedir.

```
VSWizard 8.0
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}
Param="WIZARDNAME = Wizard One"
Param="WIZARDUI = FALSE"
```

.vsz dosyasındaki parçalar aşağıda veda edileb'dir.

|Bölüm|Açıklama|
|----------|-----------------|
|Vswizard|Dosyadaki ilk parametre şablon dosyası biçiminin sürüm numarasıdır. Bu sürüm numarası 6.0, 7.0, 7.1 veya 8.0 olmalıdır. Diğer sayılar başlatılamaz ve Geçersiz Biçim hatasına neden olur.|
|Sihirbazı|Bu alan, sihirbazın OLE ProgID'ini veya alternatif olarak IDE tarafından oluşturulan sihirbazın CLSID'sinin GUID dizesini içerir.|
|Param|Bu parçalar isteğe bağlıdır. Gerektiği kadar ekleyebilirsiniz.|

Parametreler ,.vsz dosyasının sihirbaza ek özel parametreleri geçirmesini sağlar. Her değer sihirbaza varyantları bir dizi bir dize öğesi olarak geçirilir. Daha fazla bilgi için [Özel Parametreler'e](../../extensibility/internals/custom-parameters.md)bakın.

.vsz dosyanıza varsayılan yerel kimlik eklemek `FALLBACK_LCID`için, xxxx'in yerel kimliği olduğu =xxxx'i (örneğin İngilizce için 1033) belirtin. Parametre tanımlandığında, `FALLBACK_LCID` geçerli kimlik bulunamazsa sihirbaz sağlanan geri dönüş yerel kimliğini kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Parametreler](../../extensibility/internals/custom-parameters.md)
- [Sihirbazlar](../../extensibility/internals/wizards.md)
- [Şablon Dizin Açıklaması (.Vsdir) Dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

---
title: Kaynak Kontrol Eklentileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699898"
---
# <a name="source-control-plug-ins"></a>Kaynak Denetimi Eklentileri
Kaynak Kontrol Eklentisi SDK başvuru bölümü, kaynak kontrol sistemlerinin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]tümleşik olmasını sağlayan tam arabirim belirtimini içerir. Kaynak denetim eklentisinin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE) ile arabirim kurmak için uygulaması gereken çeşitli işlevler ve veri türlerinin sözdizimini ve anlamtlarını belirtir.

## <a name="in-this-section"></a>Bu Bölümde
- [Kaynak Kontrol Eklentisi API Fonksiyonları](../extensibility/source-control-plug-in-api-functions.md) Kaynak Denetimi Eklentisi API'sine uymak için kaynak denetim eklentisi tarafından uygulanması gereken işlevleri listeler.

- [IDE tarafından uygulanan geri arama işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md) Kaynak denetim eklentisinin, belirli komutlar yürütülürken bilgileri IDE'ye aktarmak için kullandığı işlevleri açıklar.

- [Sayısallaştırıcılar](../extensibility/enumerators.md) Kaynak Denetimi Eklentisi API'sinde, kaynak denetimi eklentisinin bilmesi gereken yerlandırıcı veri türlerini listeler.

- [Yetenek Bayrakları](../extensibility/capability-flags.md) Sağlayıcının `SCC_CAP_xxx` yeteneklerini gösteren bayrakları açıklar.

- [Belirli Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md) Belirli komutlar bağlamında yararlı olan bayrakları listeler.

- [Hata Kodları](../extensibility/error-codes.md) Işlevler tarafından döndürülen `SCCTRN`yaygın hata değerlerini listeler.

- [Kaynak Denetim Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeleri](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Kaynak denetim eklentisini bulmak için kayıt defterine erişmek için anahtarları açıklar.

- [MSSCCPRJ. SCC Dosyası,](../extensibility/mssccprj-scc-file.md) IDE'ye bilgi opaklığı içeren, ancak çözüm veya projeyi sürüm denetiminde bulmak için kaynak denetim eklentisi tarafından kullanılan istemci tarafı dosyasını açıklar.

- [Kaynak Kontrol Eklentisi Uygulamak Için En İyi Uygulamalar](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Kaynak Denetimi Eklentisi API'sini uygularken hatırlanması gereken önemli teknik anımsatıcılar topluluğu sağlar.

- [Dize Uzunluklarındaki Kısıtlamalar](../extensibility/restrictions-on-string-lengths.md) Kaynak Denetimi Eklentisi API'sindeki sınırlamaları çeşitli işlevlerde kullanılan dizelerin uzunlukları üzerinde açıklar.

- [Sözlük](../extensibility/source-control-plug-in-glossary.md) Kaynak Denetimi Eklentisi SDK belgelerini okumak için yararlı terimler ve tanımları sağlar.

- [Nasıl yapilir: Kaynak Denetimi Eklentileri için Uyumluluk Uyarılarını Kapat](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Uyarıları nasıl devre dışı süreceğini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Kaynak Kontrol Eklentisi Örneği](https://www.microsoft.com/download/details.aspx?id=55984) Kaynak denetimi eklentisi işlevinin bir örneğini sağlar.

- [Kaynak Kontrol Eklentileri Için Test Kılavuzu](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Kaynak denetim eklentisi ile ilgili test yordamlarını açıklar.

- [Kaynak Denetim Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md) Kaynak denetimi kullanıcı arabirimini (UI) kullanırken kaynak denetimi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] işlevselliği sağlayan bir kaynak denetimi eklentisinin nasıl oluşturulutur?

- [Visual Studio SDK Referans](../extensibility/visual-studio-sdk-reference.md) Başvuru konularının bir listesini sunar.

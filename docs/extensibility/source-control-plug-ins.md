---
title: Kaynak denetimi eklentileri | Microsoft Docs
description: Bu bölümdeki makalelerde, kaynak denetim sistemlerinin Visual Studio ile tümleştirilmesini sağlayan tüm arabirim belirtimi açıklanır.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 617b06e46bb150026f49af3e23761dfd6cb4e902
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715840"
---
# <a name="source-control-plug-ins"></a>Kaynak Denetimi Eklentileri
Kaynak denetimi eklentisi SDK 'Sı başvuru bölümü, kaynak denetim sistemlerinin ile tümleştirilebilmesine olanak tanıyan tam arabirim belirtimini içerir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Kaynak denetim eklentisinin [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamı (IDE) ile arabirim için uygulanması gereken çeşitli işlevlerin ve veri türlerinin söz dizimi ve semantiğini belirtir.

## <a name="in-this-section"></a>Bu Bölümde
- [Kaynak denetimi EKLENTISI API işlevleri](../extensibility/source-control-plug-in-api-functions.md) Kaynak denetimi eklentisi API 'siyle uyum sağlamak için kaynak denetim eklentisi tarafından uygulanması gereken işlevleri listeler.

- [IDE tarafından uygulanan geri çağırma işlevleri](../extensibility/callback-functions-implemented-by-the-ide.md) Kaynak denetimi eklentisinin, belirli komutlar yürütüldüğü sırada bilgileri IDE 'ye geri iletmek için kullandığı işlevleri açıklar.

- [Numaralandırıcılar](../extensibility/enumerators.md) Kaynak denetimi eklentisinin hakkında bilgi sahibi olması gereken kaynak denetimi eklentisi API 'sindeki Numaralandırıcı veri türlerini listeler.

- [Yetenek bayrakları](../extensibility/capability-flags.md) `SCC_CAP_xxx` Bir sağlayıcının yeteneklerini belirten bayrakları açıklar.

- [Belirli komutlar tarafından kullanılan Bitflags](../extensibility/bitflags-used-by-specific-commands.md) Belirli komutlar bağlamında yararlı olan bayrakları listeler.

- [Hata kodları](../extensibility/error-codes.md) İşlevleri tarafından döndürülen yaygın hata değerlerini listeler `SCCTRN` .

- [Kaynak denetimi eklentisini bulmak Için anahtar olarak kullanılan dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Kaynak denetimi eklentisini bulmak için kayıt defterine erişim anahtarlarını açıklar.

- [Mssccprj. SCC dosyası](../extensibility/mssccprj-scc-file.md) IDE 'de donuk bilgiler içeren bir istemci tarafı dosyası tanımlar, ancak bu, sürüm denetimindeki çözümü veya projeyi bulmak için kaynak denetim eklentisi tarafından kullanılır.

- [Kaynak denetim eklentisi uygulamak Için En Iyi uygulamalar](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Kaynak denetimi eklentisi API 'SI uygulanırken dikkat etmeniz gereken önemli bir teknik anımsatıcı koleksiyonu sağlar.

- [Dize uzunlukları kısıtlamaları](../extensibility/restrictions-on-string-lengths.md) Çeşitli işlevlerde kullanılan dizelerin uzunluklarıyla kaynak denetimi eklentisi API 'sindeki sınırlamaları açıklar.

- [Sözlük](../extensibility/source-control-plug-in-glossary.md) Kaynak denetimi eklentisi SDK belgelerini okumak için faydalı terimler ve bunların tanımlarını sağlar.

- [Nasıl yapılır: kaynak denetimi eklentileri Için uyumluluk uyarılarını](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) kapatma Uyarıların nasıl devre dışı bırakılacağını açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Kaynak denetimi eklentisi örneği](https://www.microsoft.com/download/details.aspx?id=55984) Kaynak denetimi eklentisi işlevlerinin bir örneğini sağlar.

- [Kaynak denetimi eklentileri Için Test Kılavuzu](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Kaynak denetimi eklentisiyle ilgili test yordamlarını açıklar.

- [Kaynak denetimi eklentisi oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md) Kaynak denetimi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Kullanıcı arabirimini (UI) kullanırken kaynak denetimi işlevselliği sağlayan bir kaynak denetimi eklentisinin nasıl oluşturulacağını açıklar.

- [Visual STUDIO SDK başvurusu](../extensibility/visual-studio-sdk-reference.md) Başvuru konularının bir listesini gösterir.

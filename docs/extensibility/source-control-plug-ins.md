---
title: Kaynak Denetimi Eklentileri | Microsoft Docs
description: Bu bölümdeki makalelerde, kaynak denetim sistemlerinin kaynak denetimi sistemleriyle tümleştirilene tam arabirim belirtimi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1a16c639e069409bdb4004b1d8680a3361d65c3c04ca13c18c82e94ae1b52eab
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121259922"
---
# <a name="source-control-plug-ins"></a>Kaynak Denetimi Eklentileri
Kaynak Denetimi Eklentisi SDK'sı başvuru bölümü, kaynak denetim sistemlerinin ile tümleştirilemesi için tam arabirim belirtimi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] içerir. Kaynak denetimi eklentisinin tümleşik geliştirme ortamı (IDE) ile arabirim için uygulaması gereken çeşitli işlevlerin ve veri türlerinin söz dizimlerini ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] semantiklerini belirtir.

## <a name="in-this-section"></a>Bu Bölümde
- [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md) Kaynak Denetimi Eklentisi API'sini uyumlu olması için kaynak denetimi eklentisi tarafından uygulanması gereken işlevleri listeler.

- [IDE Tarafından Uygulanan Geri Çağırma İşlevleri](../extensibility/callback-functions-implemented-by-the-ide.md) Kaynak denetimi eklentisinin, belirli komutlar yürütülürken bilgileri IDE'ye geri almak için kullandığı işlevleri açıklar.

- [Numaralayıcılar](../extensibility/enumerators.md) Kaynak denetimi eklentisinin biliyor olması gereken Kaynak Denetimi Eklentisi API'sinde numaralayıcı veri türlerini listeler.

- [Yetenek Bayrakları](../extensibility/capability-flags.md) Sağlayıcının `SCC_CAP_xxx` özelliklerini gösteren bayrakları açıklar.

- [Belirli Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md) Belirli komutlar bağlamında yararlı olan bayrakları listeler.

- [Hata Kodları](../extensibility/error-codes.md) İşlevler tarafından olarak döndürülen yaygın hata değerlerini `SCCTRN` listeler.

- [Kaynak Denetimi Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Kaynak denetimi eklentisini bulmak için kayıt defterine erişim anahtarlarını açıklar.

- [MSSCCPRJ. SCC](../extensibility/mssccprj-scc-file.md) Dosyası IDE'ye opak bilgiler içeren, ancak kaynak denetimi eklentisi tarafından sürüm denetiminde çözümü veya projeyi bulmak için kullanılan bir istemci tarafı dosyasını açıklar.

- [Kaynak Denetimi Eklentisi Uygulamak için En İyi Yöntemler](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Kaynak Denetimi Eklentisi API'sini uygulama sırasında anımsanacak önemli teknik anımsatıcılar koleksiyonu sağlar.

- [Dize Uzunlukları Kısıtlamaları](../extensibility/restrictions-on-string-lengths.md) Kaynak Denetimi Eklentisi API'sinde çeşitli işlevlerde kullanılan dizelerin uzunlukları ile ilgili sınırlamaları açıklar.

- [Sözlük](../extensibility/source-control-plug-in-glossary.md) Kaynak Denetimi Eklentisi SDK'sı belgelerini okumak için yararlı terimler ve tanımları sağlar.

- [Nasıl olur: Kaynak Denetimi Eklentileri için Uyumluluk Uyarılarını Kapatma](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Uyarıları devre dışı bırakmayı açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Kaynak Denetimi Eklentisi Örneği](https://www.microsoft.com/download/details.aspx?id=55984) Kaynak denetimi eklentisi işlevinin bir örneğini sağlar.

- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Kaynak denetimi eklentisiyle ilgili test yordamlarını açıklar.

- [Kaynak Denetimi Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md) Kaynak denetimi kullanıcı arabirimini (UI) kullanırken kaynak denetimi işlevselliği sağlarken kaynak denetimi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eklentisinin nasıl oluşturulacaklarını açıklar.

- [Visual Studio SDK Başvurusu](../extensibility/visual-studio-sdk-reference.md) Başvuru konularının listesini sunar.

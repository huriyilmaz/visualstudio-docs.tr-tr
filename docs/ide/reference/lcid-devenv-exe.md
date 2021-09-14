---
title: -LCID (devenv.exe)
description: IDE içindeki metin, para birimi ve diğer değerler için kullanılan varsayılan dili ayarlamak üzere LCID devenv komut satırı anahtarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /L switch
- Devenv, /LCID switch
- locale IDs
- L Devenv switch
- /L Devenv switch
- LCID devenv switch
- /LCID Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 35a8fa0a783817d5ad1fdc4b6bce39f873a051f1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628749"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)

IDE içindeki metin, para birimi ve diğer değerler için kullanılan varsayılan dili ayarlar.

## <a name="syntax"></a>Söz dizimi

```shell
devenv {/LCID|/L} LocaleID
```

## <a name="arguments"></a>Bağımsız değişkenler

- *Localeıd*

  Gereklidir. Belirttiğiniz dilin yerel dil tanımlayıcısı (LCID).

## <a name="remarks"></a>Açıklamalar

IDE'i yükler ve ortam için varsayılan doğal dili ayarlar. Bu değişiklik oturumlar arasında kalıcıdır ve IDE bu değişikliği **Araçlar** Seçenekler Ortamı Uluslararası Ayarlar  >    >    >    >  **Dil kutusunda** gösterir.

Belirtilen dil sisteminiz üzerinde kullanılamıyorsa anahtar `/LCID` yoksayılır.

Aşağıdaki tabloda, Visual Studio tarafından desteklenen dillerin LCID'leri liste Visual Studio.

|Dil|LCID|
|--------------|----------|
|Basitleştirilmiş Çince|2052|
|Geleneksel Çince|1028|
|Çekçe|1029|
|İngilizce|1033|
|Fransızca|1036|
|Almanca|1031|
|İtalyanca|1040|
|Japonca|1041|
|Korece|1042|
|Lehçe|1045|
|Portekizce (Brezilya)|1046|
|Rusça|1049|
|İspanyolca|3082|
|Türkçe|1055

## <a name="example"></a>Örnek

Bu örnek, İngilizce kaynak dizeleriyle IDE'leri yükler.

```shell
devenv /LCID 1033
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [Uluslararası Ayarlar, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/international-settings-environment-options-dialog-box.md)
- [Pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)

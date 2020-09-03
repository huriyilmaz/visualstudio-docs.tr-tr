---
title: -LCıD (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: badb88abdf4b3ffd6140cb587b2b0add20630925
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672696"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Metin, para birimi ve tümleşik geliştirme ortamı (IDE) içindeki diğer değerler için kullanılan varsayılan dili ayarlar.

## <a name="syntax"></a>Söz dizimi

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>Bağımsız değişkenler
 `LocaleID` Gerekli. Belirttiğiniz dilin LCıD (Yerel KIMLIK).

## <a name="remarks"></a>Açıklamalar
 IDE 'yi yükler ve ortam için varsayılan doğal dili ayarlar. Bu değişiklik oturumlar arasında kalıcı hale getirilir ve IDE 'deki **Seçenekler** Iletişim kutusunda **ortam** seçeneklerinin **Uluslararası ayarlar** bölmesinde yansıtılır.

 Belirtilen dil kullanıcının sisteminde yoksa,/LCıD anahtarı yok sayılır.

 Aşağıdaki tabloda tarafından desteklenen dillerin LCID 'Ler listelenmiştir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

|Dil|LCID|
|--------------|----------|
|Basitleştirilmiş Çince|2052|
|Geleneksel Çince|1028|
|İngilizce|1033|
|Fransızca|1036|
|Almanca|1031|
|İtalyanca|1040|
|Japonca|1041|
|Korece|1042|
|İspanyolca|3082|

## <a name="example"></a>Örnek
 Bu örnek, IDE 'yi Ingilizce kaynak dizeleri ile yükler.

```
devenv /LCID 1033
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [Uluslararası ayarlar, ortam, Seçenekler iletişim kutusu](../../ide/reference/international-settings-environment-options-dialog-box.md) [pencere düzenlerini özelleştirme](../../ide/customizing-window-layouts-in-visual-studio.md)

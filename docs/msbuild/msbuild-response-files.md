---
title: MSBuild Yanıt dosyaları | Microsoft Docs
description: MSBuild.exe komut satırı anahtarları içeren MSBuild response veya. rsp dosyaları, metin dosyaları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0037b8ca17b8f1a3ed5756f7916b72c581b67e325f9a44b3e4b016a34ea07f88
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121302870"
---
# <a name="msbuild-response-files"></a>MSBuild yanıt dosyaları

Yanıt (*. rsp*) dosyaları *MSBuild.exe* komut satırı anahtarları içeren metin dosyalarıdır. Her anahtar ayrı bir satırda olabilir veya tüm anahtarlar tek bir satırda olabilir. Açıklama satırları bir sembol ile önceden başlar **#** . **@** Anahtar, *MSBuild.exe* başka bir yanıt dosyası geçirmek için kullanılır.

## <a name="msbuildrsp"></a>MSBuild. rsp

Otomatik yanıt dosyası, *MSBuild.exe* otomatik olarak bir proje oluştururken kullanılan özel bir *. rsp* dosyasıdır. bu dosya, *MSBuild. rsp*, *MSBuild.exe* aynı dizinde olmalıdır, aksi halde bulunamamıştır. Bu dosyayı, *MSBuild.exe* için varsayılan komut satırı anahtarlarını belirtmek üzere düzenleyebilirsiniz. örneğin, her proje oluşturduğunuzda aynı günlükçüsü kullanırsanız, **-günlükçü** anahtarını *MSBuild. rsp* öğesine ekleyebilirsiniz ve *MSBuild.exe* bir proje oluşturulduğunda günlükçü kullanılır.

## <a name="directorybuildrsp"></a>Directory. Build. rsp

sürüm 15,6 ve üzeri sürümlerde, MSBuild *Directory. Build. rsp* adlı bir dosya için projenin üst dizinlerinde arama yapılır.  Bu, komut satırı derlemeleri sırasında varsayılan bağımsız değişkenler sağlamak için bir kaynak kod deposunda yararlı olabilir.  Barındırılan yapıların komut satırı bağımsız değişkenlerini belirtmek için de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)

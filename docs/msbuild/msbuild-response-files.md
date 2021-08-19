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
ms.openlocfilehash: abe7882e18936b169cfcd0b02e7eaa66c891f5a2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085019"
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

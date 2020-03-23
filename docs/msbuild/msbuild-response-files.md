---
title: MSBuild Yanıt Dosyaları | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d6e3c77fee53b15ec8d18cb74fd7355ee101a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302898"
---
# <a name="msbuild-response-files"></a>MSBuild yanıt dosyaları

Yanıt (*.rsp*) dosyaları *MSBuild.exe* komut satırı anahtarları içeren metin dosyalarıdır. Her anahtar ayrı bir hatta veya tüm anahtarlar tek bir satırda olabilir. Açıklama satırları bir **#** sembolle önceden yazılmıştır. Anahtar **@** *MSBuild.exe*başka bir yanıt dosyası geçmek için kullanılır.

## <a name="msbuildrsp"></a>MSBuild.rsp

Otomatik yanıt dosyası, *MSBuild.exe'nin* proje oluştururken otomatik olarak kullandığı özel bir *.rsp* dosyasıdır. Bu dosya, *MSBuild.rsp*, *MSBuild.exe*ile aynı dizinde olmalıdır, aksi takdirde bulunamaz. Varsayılan komut satırı anahtarlarını *MSBuild.exe*olarak belirtmek için bu dosyayı düzenleyebilirsiniz. Örneğin, bir proje yi her oluşturduğunuzda aynı logger kullanıyorsanız, *MSBuild.rsp'ye* **-logger** anahtarını ekleyebilirsiniz ve *MSBuild.exe* her proje inşa ediş olduğunda logger'ı kullanır.

## <a name="directorybuildrsp"></a>Dizin.Build.rsp

Sürüm 15.6 ve üzeri, MSBuild *Directory.Build.rsp*adlı bir dosya için projenin üst dizinleri arayacaktır.  Bu komut satırı yapılar sırasında varsayılan bağımsız değişkenleri sağlamak için bir kaynak kodu deposunda yararlı olabilir.  Barındırılan yapıların komut satırı bağımsız değişkenlerini belirtmek için de kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)

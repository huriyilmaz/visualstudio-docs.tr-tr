---
title: Kod parçacıkları sorunlarını giderme
description: Genellikle kod parçacığı dosyasındaki veya bozuk bir kod parçacığı dosyasındaki hatalı içeriğin neden olduğu IntelliSense kod parçacıkları ile ilgili sorunların nasıl giderileceği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4012298bdc4edf0c174576c739e67781bfffdade
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479218"
---
# <a name="troubleshoot-snippets"></a>Kod parçacıkları sorunlarını giderme

IntelliSense kod parçacıkları ile ilgili sorunlar genellikle iki sorun nedeniyle oluşur: bozuk parçacık dosyası veya kod parçacığı dosyasındaki bozuk içerik.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Kod parçacığı dosya Gezgini 'nden bir Visual Studio kaynak dosyasına sürüklenemiyor

- Kod parçacığı dosyasındaki XML bozuk olabilir. İçindeki **XML Düzenleyicisi** , [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] XML yapısındaki sorunları bulabilir.

- Kod parçacığı dosyası, kod parçacığı şemasıyla uyumlu olmayabilir. İçindeki **XML Düzenleyicisi** , [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] XML yapısındaki sorunları bulabilir.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kodda vurgulanmayan derleyici hataları var

- Proje başvurunuz eksik olabilir. Kod parçacığı hakkındaki belgeleri inceleyin. Başvuru bilgisayarda bulunamazsa, yüklemeniz gerekir. Bir kod parçacığının eklenmesi, gerekli tüm başvuruları projeye eklememelidir. Kod parçacığında başvuru bilgileri eksikse, hata olarak kod parçacığı oluşturucuya raporlanabilir.

- Bir değişken tanımsız olabilir. Kod parçacığında tanımsız değişkenler vurgulanmalıdır. Aksi takdirde, hata olarak kod parçacığı oluşturucuya rapor edilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)

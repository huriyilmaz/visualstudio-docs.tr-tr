---
title: Sorun giderme parçacıkları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f73cb7ba59daf2f8ee957d95dee36bba59f87614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654788"
---
# <a name="troubleshooting-snippets"></a>Sorun Giderme Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense kod parçacıkları ile ilgili sorunlar genellikle iki sorun nedeniyle oluşur: bozuk parçacık dosyası veya kod parçacığı dosyasındaki bozuk içerik.

## <a name="common-problems"></a>Yaygın sorunlar

### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Kod parçacığı dosya Gezgini 'nden bir Visual Studio kaynak dosyasına Sürüklenemiyor

- Kod parçacığı dosyasındaki XML bozuk olabilir. İçindeki **XML Düzenleyicisi** , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] XML yapısındaki sorunları bulabilir.

- Kod parçacığı dosyası, kod parçacığı şemasıyla uyumlu olmayabilir. İçindeki **XML Düzenleyicisi** , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] XML yapısındaki sorunları bulabilir.

### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kodda vurgulanmayan derleyici hataları var

- Proje başvurunuz eksik olabilir. Kod parçacığı hakkındaki belgeleri inceleyin. Başvuru bilgisayarda bulunamazsa, yüklemeniz gerekir. Bir kod parçacığının eklenmesi, gerekli tüm başvuruları projeye eklememelidir. Kod parçacığında başvuru bilgileri eksikse, hata olarak kod parçacığı oluşturucuya raporlanabilir.

- Bir değişken tanımsız olabilir. Kod parçacığında tanımsız değişkenler vurgulanmalıdır. Aksi takdirde, hata olarak kod parçacığı oluşturucuya rapor edilebilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod Parçacıkları](../ide/code-snippets.md)

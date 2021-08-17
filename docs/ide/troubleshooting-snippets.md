---
title: Kod parçacıkları sorunlarını giderme
description: Kod parçacığı dosyasındaki hatalı içerik veya bozuk bir kod parçacığı dosyasından kaynaklanan IntelliSense kod parçacıklarıyla ilgili sorunları gidermeyi öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4126adddbadf9e117a9070813f1bc227c0cff271f8863cb59c3b60777a775b93
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231944"
---
# <a name="troubleshoot-snippets"></a>Kod parçacıkları sorunlarını giderme

IntelliSense kod parçacıklarıyla ilgili sorunlar genellikle iki sorundan kaynak olur: bozuk bir kod parçacığı dosyası veya kod parçacığı dosyasındaki bozuk içerik.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Kod parçacığı, Dosya Gezgini kaynak Visual Studio sürüklenmez

- Kod parçacığı dosyasındaki XML bozuk olabilir. içinde **XML** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Düzenleyicisi, XML yapısında sorunları bulabilirsiniz.

- Kod parçacığı dosyası kod parçacığı şemasına uygun olabilir. içinde **XML** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Düzenleyicisi, XML yapısında sorunları bulabilirsiniz.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kodda vurgulanmış derleyici hataları var

- Bir proje başvurusu eksik olabilir. Kod parçacığıyla ilgili belgeleri inceleyin. Başvuru bilgisayarda bulunamasa, bunu yüklemeniz gerekir. Bir kod parçacığı eklemek, projeye gereken tüm başvuruları eklemeli. Kod parçacığında başvuru bilgileri eksikse, kod parçacığı oluşturucuya hata olarak bildirebilirsiniz.

- Değişken tanımlanmamış olabilir. Bir kod parçacığında tanımlanmamış değişkenler vurgulanmış olması gerekir. Yoksa, bu kod parçacığı oluşturucuya bir hata olarak bildirleştirilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)

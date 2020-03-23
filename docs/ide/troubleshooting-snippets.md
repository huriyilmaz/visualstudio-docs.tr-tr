---
title: Kod parçacıkları sorunlarını giderme
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
ms.openlocfilehash: a699c6a158b5a0751824c7634ddd637467da50d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588700"
---
# <a name="troubleshoot-snippets"></a>Kod parçacıkları sorunlarını giderme

IntelliSense kod parçacıklarıile ilgili sorunlar genellikle iki sorundan kaynaklanır: bozuk bir parçacık dosyası veya parçacık dosyasındaki kötü içerik.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Parçacık Dosya Gezgini'nden Visual Studio kaynak dosyasına sürülemiyor

- Parçacık dosyasındaki XML bozuk olabilir. **XML** Düzenleyicisi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] XML yapısındaki sorunları bulabilir.

- Parçacık dosyası snippet şemasına uymayabilir. **XML** Düzenleyicisi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] XML yapısındaki sorunları bulabilir.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Kod vurgulanmaz derleyici hataları vardır

- Proje başvurusu eksik olabilir. Parçacıkla ilgili belgeleri inceleyin. Başvuru bilgisayarda bulunmazsa, yüklemeniz gerekir. Bir snippet ekleme projeye gerekli başvuruları eklemelidir. Parçacık başvuru bilgilerini eksikse, bu hata olarak parçacık oluşturucuya bildirilebilir.

- Bir değişken tanımlanmamış olabilir. Bir snippet'teki tanımlanmamış değişkenler vurgulanmalıdır. Değilse, bu bir hata olarak parçacık oluşturucuya bildirilebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları](../ide/code-snippets.md)

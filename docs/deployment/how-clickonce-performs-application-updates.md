---
title: ClickOnce uygulama güncelleştirmelerini nasıl gerçekleştirir | Microsoft Docs
description: ClickOnce 'ın, uygulamayı güncelleştirip güncelleştirmeyeceğine karar vermek için dosya sürüm bilgilerini nasıl kullandığını öğrenin. ClickOnce, indirme sırasında yedekliliği önlemek için dosya düzeltme eki uygulamayı kullanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0177f199f0178e9fe0221a4cb6daa58d36a6f87
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382674"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce uygulama güncelleştirmelerini nasıl gerçekleştirir
ClickOnce, uygulamanın dosyalarını güncelleştirip güncelleştirmeyeceğine karar vermek için uygulamanın dağıtım bildiriminde belirtilen dosya sürümü bilgilerini kullanır. Güncelleştirme başladıktan sonra ClickOnce, uygulama dosyalarının gereksiz şekilde indirilmesini önlemek için *Dosya düzeltme eki* adlı bir teknik kullanır.

## <a name="file-patching"></a>Dosya düzeltme eki uygulama
 Bir uygulamayı güncelleştirirken, dosyalar değiştirilmediği takdirde ClickOnce, uygulamanın yeni sürümü için tüm dosyaları indirmez. Bunun yerine, geçerli uygulamanın uygulama bildiriminde belirtilen dosyaların karma imzalarını, yeni sürüm için bildirimdeki imzalara karşı karşılaştırır. Bir dosyanın imzaları farklıysa, ClickOnce yeni sürümü indirir. İmzalar eşleşirse, dosya bir sürümden sonrakine değiştirilmez. Bu durumda, ClickOnce var olan dosyayı kopyalar ve uygulamanın yeni sürümünde kullanır. Bu yaklaşım, yalnızca bir veya iki dosya değişmiş olsa bile ClickOnce 'ın tüm uygulamayı yeniden indirmesini önler.

 Dosya düzeltme eki uygulama ve yöntemleri kullanılarak isteğe bağlı olarak indirilen derlemeler için de kullanılabilir <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> .

 Uygulamanızı derlemek için Visual Studio kullanıyorsanız, tüm projeyi yeniden oluşturduğunuzda tüm dosyalar için yeni karma imzalar oluşturur. Bu durumda, tüm derlemeler istemciye indirilir, ancak yalnızca birkaç derleme değişmiş olabilir.

 Dosya düzeltme eki uygulama, veri olarak işaretlenmiş ve veri dizininde depolanan dosyalar için çalışmaz. Bunlar, dosyanın karma imzasına bakılmaksızın her zaman indirilir. Veri dizini hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarında yerel ve uzak verilere erişme](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
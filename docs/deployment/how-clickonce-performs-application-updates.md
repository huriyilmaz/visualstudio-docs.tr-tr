---
title: ClickOnce Güncelleştirmelerini Nasıl Gerçekleştirir| Microsoft Docs
description: Uygulamanın ClickOnce olup olmadığını öğrenmek için dosya sürümü bilgilerini nasıl kullandığını öğrenin. ClickOnce, indirmede yedekliliği önlemek için dosya düzeltme eki uygulama kullanır.
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 046348ed2f6e8425434291454bb2162aac5c0f82
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128058"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce uygulama güncelleştirmelerini nasıl gerçekleştirir
ClickOnce, uygulamanın dosyalarını güncelleştirip güncelleştirmey karar vermek için uygulamanın dağıtım bildiriminde belirtilen dosya sürümü bilgilerini kullanır. Güncelleştirme başladıktan sonra, ClickOnce dosyaları yedekli olarak indiriledikten kaçınmak için dosya düzeltme eki uygulama olarak adlandırılan bir teknik kullanılır. 

## <a name="file-patching"></a>Dosya düzeltme eki uygulama
 Bir uygulamayı ClickOnce, dosyalar değişmediği sürece uygulamanın yeni sürümü için tüm dosyaları indirmez. Bunun yerine, geçerli uygulama için uygulama bildiriminde belirtilen dosyaların karma imzalarını yeni sürümün bildiriminde yer alan imzalarla karşılar. Bir dosyanın imzaları farklı ise ClickOnce sürümü indirir. İmzalar eş olursa dosya bir sürümden sonraki sürüme değişmemiştir. Bu durumda, ClickOnce dosyayı kopyalar ve uygulamanın yeni sürümünde kullanır. Bu yaklaşım, ClickOnce veya iki dosya değiştirilmiş olsa bile uygulamanın tamamını yeniden indirmek zorunda kalmadan önce bu yaklaşımın önüne geçmektedir.

 Dosya düzeltme eki uygulama, ve yöntemleri kullanılarak isteğe bağlı olarak indirilen <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> derlemeler <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> için de çalışır.

 Uygulamanızı derlemek Visual Studio kullanırsanız, projenin tamamını her yeniden derleye her derleyeyde tüm dosyalar için yeni karma imzalar oluşturulur. Bu durumda, yalnızca birkaç derleme değişmiş olsa da, tüm derlemeler istemciye indirilir.

 Dosya düzeltme eki uygulama, veri olarak işaretlenen ve veri dizininde depolanan dosyalar için çalışmıyor. Bunlar dosyanın karma imzasını ne olursa olsun her zaman indirilir. Veri dizini hakkında daha fazla bilgi için [bkz. Uygulama uygulamalarında yerel ve uzak ClickOnce erişme.](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce dağıtım stratejisini seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)
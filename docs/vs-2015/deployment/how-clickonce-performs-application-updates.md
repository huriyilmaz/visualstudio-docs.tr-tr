---
title: ClickOnce uygulama güncelleştirmelerini nasıl gerçekleştirir | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2e8a3c1054219bb7d5b0f9a9ef5e710786344e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152840"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce Uygulama Güncelleştirmelerini Nasıl Gerçekleştirir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce, uygulamanın dosyalarını güncelleştirip güncelleştirmeyeceğine karar vermek için uygulamanın dağıtım bildiriminde belirtilen dosya sürümü bilgilerini kullanır. Güncelleştirme başladıktan sonra ClickOnce, uygulama dosyalarının gereksiz şekilde indirilmesini önlemek için *Dosya düzeltme eki* adlı bir teknik kullanır.  
  
## <a name="file-patching"></a>Dosya düzeltme eki uygulama  
 Bir uygulamayı güncelleştirirken, dosyalar değiştirilmediği takdirde ClickOnce, uygulamanın yeni sürümü için tüm dosyaları indirmez. Bunun yerine, geçerli uygulamanın uygulama bildiriminde belirtilen dosyaların karma imzalarını, yeni sürüm için bildirimdeki imzalara karşı karşılaştırır. Bir dosyanın imzaları farklıysa, ClickOnce yeni sürümü indirir. İmzalar eşleşirse, dosya bir sürümden sonrakine değiştirilmez. Bu durumda, ClickOnce var olan dosyayı kopyalar ve uygulamanın yeni sürümünde kullanır. Bu yaklaşım, yalnızca bir veya iki dosya değişmiş olsa bile ClickOnce 'ın tüm uygulamayı yeniden indirmesini önler.  
  
 Dosya düzeltme eki uygulama ve yöntemleri kullanılarak isteğe bağlı olarak indirilen derlemeler için de kullanılabilir <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> .  
  
 Uygulamanızı derlemek için Visual Studio kullanıyorsanız, tüm projeyi yeniden oluşturduğunuzda tüm dosyalar için yeni karma imzalar oluşturur. Bu durumda, tüm derlemeler istemciye indirilir, ancak yalnızca birkaç derleme değişmiş olabilir.  
  
 Dosya düzeltme eki uygulama, veri olarak işaretlenmiş ve veri dizininde depolanan dosyalar için çalışmaz. Bunlar, dosyanın karma imzasına bakılmaksızın her zaman indirilir. Veri dizini hakkında daha fazla bilgi için bkz. [ClickOnce uygulamalarında yerel ve uzak verilere erişme](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce Dağıtım Stratejisini Seçme](../deployment/choosing-a-clickonce-deployment-strategy.md)

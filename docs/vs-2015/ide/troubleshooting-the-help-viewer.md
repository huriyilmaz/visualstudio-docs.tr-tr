---
title: Yardım Görüntüleyicisi sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: troubleshooting
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2cedc9f45d2e21684496bd882de4aa74b3bf8b3d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851074"
---
# <a name="troubleshooting-the-help-viewer"></a>Yardım Görüntüleyici'de Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda, yardım görüntüleyiciyle karşılaşabileceğiniz sorunlar ele alınmaktadır.

## <a name="audio-doesnt-work"></a>Ses çalışmıyor.
 Yardım Görüntüleyici bir ses oynatıcı içermez. Ses içeren içeriği indirdiğinizde, **Çalıştır**' ı seçtiğinizde hiçbir şey gerçekleşmezse, bir ses oynatıcı yükleyin.

## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>Arama, Windows Server 2008, Windows Server 2008 SP1 veya Windows Server 2008 R2 'de çalışmaz.
 Yardım görüntüleyicisinde arama ve filtreleme özellikleri Windows Search hizmetinin yüklü ve açık olmasını gerektirir. Varsayılan olarak, bu hizmet Windows Server 2008, Windows Server 2008 with Service Pack 1 (SP1) ve Windows Server 2008 R2 ' de kapalıdır.

#### <a name="to-activate-windows-search-service"></a>Windows Search hizmetini etkinleştirmek için

1. Sunucu Yöneticisi'ni başlatın.

2. Sol gezinti bölmesinde **Roller**' i seçin.

3. Roller Özeti bölmesinde **Rol Ekle**' yi seçin.

4. Dosya Hizmetleri rolünü seçin ve sonra **İleri** düğmesini seçin.

5. Windows Search rol hizmetini seçin.

## <a name="additional-resources"></a>Ek Kaynaklar
 Aşağıdaki kaynakları kullanarak daha fazla bilgi alabilir ve Yardım Görüntüleyicisi hakkında geri bildirim sağlayabilirsiniz:

- Geri bildirim sağlamak için Microsoft Web sitesinde [Microsoft Connect](https://connect.microsoft.com/) 'e bakın veya [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com)e-posta gönderin.

- Daha fazla bilgi için [Geliştirici belgelerine ve yardım sistemi](https://social.msdn.microsoft.com/Forums/en-US/devdocs/threads) forumuna ve [Yardım Guy](https://blogs.msdn.com/b/thehelpguy/) bloguna bakın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Yardım Görüntüleyicisi 2,1 Yönetici Kılavuzu](https://msdn.microsoft.com/library/hh492077(VS.110).aspx)

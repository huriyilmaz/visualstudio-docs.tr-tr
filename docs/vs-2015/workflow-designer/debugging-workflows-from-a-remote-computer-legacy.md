---
title: Uzak bilgisayardan Iş akışlarında hata ayıklama (eski) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656853"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Uzak Bir Bilgisayardan İş Akışlarında Hata Ayıklama (Eski)
Bu konu başlığı altında, eski [!INCLUDE[wfd1](../includes/wfd1-md.md)] oluşturulan uzak eski [!INCLUDE[wf](../includes/wf-md.md)] uygulamalarının hatalarını ayıklama açıklanmaktadır. Uygulamanızın [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] veya [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] hedeflemesini gerektiren eski [!INCLUDE[wfd2](../includes/wfd2-md.md)] kullanın.

 @No__t_0 yüklediğinizde, bileşen yükleme seçeneklerinden biri [!INCLUDE[wf](../includes/wf-md.md)] için [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] hata ayıklayıcıyı yüklemektir. Bu, uzaktan hata ayıklama bileşenlerini yüklüyor. Bu uzaktan hata ayıklama bileşenlerinin uzak iş akışı hata ayıklaması için hedeflediğiniz bilgisayarda yüklü olması gerekir.

 Ek olarak, uzak bir bilgisayarda hata ayıklamanın bulunduğu eski iş akışının iş akışı tanımını içeren derleme, hata ayıkladığınız yerel bilgisayarın genel derleme önbelleğinde (GAC) yüklü olmalıdır. Örneğin, bir uzak bilgisayarda eski bir iş akışı çalışıyorsa ve B yerel bilgisayarından hata ayıklaması yapıyorsanız, iş akışı tanımının B bilgisayarının GAC 'de mevcut olması gerekir. Bu, tasarımcı 'nın B bilgisayarı üzerinde uzaktan çalışan iş akışının iş akışı işaretlemesini ve bilgisayar B üzerinde görüntülenmesini sağlar. Genel derleme önbelleği hakkında daha fazla bilgi için MSDN Kitaplığı ' na bakın.

 [!INCLUDE[wf2](../includes/wf2-md.md)] uzaktan hata ayıklama işlevleri, diğer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bileşenleri için uzaktan hata ayıklamayla aynı şekilde çalışır. Daha fazla bilgi için bkz. MSDN Kitaplığı 'nda uzaktan hata ayıklama [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].

## <a name="see-also"></a>Ayrıca Bkz.
 [Eski İş Akışlarında Hata Ayıklama](../workflow-designer/debugging-legacy-workflows.md)
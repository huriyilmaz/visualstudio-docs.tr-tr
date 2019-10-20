---
title: Kod ölçümleri sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eda4127e046c7676525f1755f148663f58ec9b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672074"
---
# <a name="troubleshooting-code-metrics-issues"></a>Kod Ölçümleri Sorunlarını Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod ölçümleri topladığınızda aşağıdaki sorunlardan bazılarını yaşayabilirsiniz:

- [Visual Studio 2010 kod karmaşıklığı hesaplamalarında yapılan değişiklikler](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Visual Studio 2010 kod karmaşıklığı hesaplamalarında yapılan değişiklikler

Aynı işlev için, [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] içinde hesaplanan kod karmaşıklığı ölçümü aşağıdaki durumlar için önceki [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sürümleriyle hesaplanan ölçüden farklı olabilir:

- İşlev bir veya daha fazla catch bloğu içeriyor. @No__t_0 önceki sürümlerinde, catch blokları hesaplamaya eklenmedi. @No__t_0, her bir catch bloğunun karmaşıklığı işlevin karmaşıklığına eklenir.

- İşlev, bir anahtar (VB 'de Case, Select Case) ifadesini içerir. @No__t_0 ve önceki sürümler arasındaki derleyici farklılıkları, dönüş durumları içeren bazı Switch deyimleri için farklı MSIL kodu oluşturabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Kodun Ölçüm Karmaşıklığı ve Bakımı](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

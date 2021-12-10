---
title: 'Nasıl yapılır: Çoklu başlangıç projeleri ayarlama'
description: Hata ayıklayıcıyı Visual Studio proje çalıştırmayı belirtmenize nasıl izin verir?
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: how-to
helpviewer_keywords:
- startup projects, setting multiple startup projects
ms.assetid: 6131eb80-8745-4eb9-bdab-433e69b41651
ms.technology: vs-ide-compile
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8816ec16e1424ab6b7a27e16c750085a794b3cdf
ms.sourcegitcommit: 99e0146dfe742f6d1955b9415a89c3d1b8afe4e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2021
ms.locfileid: "134554043"
---
# <a name="how-to-set-multiple-startup-projects"></a>Nasıl yapılır: Çoklu başlangıç projeleri ayarlama

Visual Studio **F5** (Hata Ayıklama ile Başla) veya **Ctrl** F5 (Hata ayıklama olmadan başlat) tuşlarına bastığınızda birden fazla projenin nasıl çalıştırıldığından emin olabilir veya araç çubuğu düğmesini kullanarak +  uygulamanızı başlatabilirsiniz. Bu şekilde, bir hata ayıklama oturumu sırasında ya da yalnızca yerel olarak çalıştırarak ve test etme sırasında birbirlerine bağlı olan birden çok site, uygulama veya hizmeti doğru şekilde başlatabilirsiniz.

## <a name="to-set-multiple-startup-projects"></a>Birden çok başlangıç projesi ayarlamak için

1. Bu **Çözüm Gezgini** çözümü (en üst düğüm) seçin.

2. Çözüm düğümünün bağlamını (sağ tıklama) seçin ve ardından Özellikler'i **seçin.** Çözüm **Özellik Sayfaları** iletişim kutusu görüntülenir.

3. Ortak Özellikler **düğümünü genişletin** ve Başlangıç **özellikleri'Project.**

4. Birden Çok **Başlangıç Projesi seçeneğini** belirleyin ve uygun eylemleri ayarlayın.

:::moniker range=">=vs-2019"

## <a name="example"></a>Örnek

Aşağıdaki örnekte üç proje, bir ön uç web sitesi, bir Web API'si projesi ve bir web uygulaması projesine sahip bir WebFrontEndA Docker Compose yer almaktadır. Aşağıdaki ekran görüntüsünde, biri hata ayıklamalı, biri de olmadan olmak üzere üç projeden iki tane başlatma adımları yer a açıklamalı:

![Çözüm Özellik Sayfalarının ekran görüntüsü.](media/vs-2022/startup-projects.png)

Bu örnekte ve diğer Docker Compose senaryolarda, tek başlangıç projesi olarak seçerseniz, ancak başlatacak projeleri veya hizmetleri belirtmek için farklı bir `docker-compose` yol kullanacağız. Hangi hizmetlerin başlatıp Docker Compose, hata ayıklayıcının ekli olup olmadığını belirlemek için bir Docker Compose başlatma profili kullanır ve yapılandırmaya yönelik Visual Studio iletişim kutusu vardır. Bkz. [Hizmetlerin bir alt kümesini başlatma.](../containers/launch-profiles.md) Çözüm **Özellik Sayfaları iletişim** kutusu yalnızca kapsayıcılı olmayan çözümler  için veya başlatmayı yönetmek için Docker Compose için kullanılır.
:::moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme ve oluşturma](../ide/compiling-and-building-in-visual-studio.md)
- [Çözüm ve projelerle çalışma](../ide/creating-solutions-and-projects.md)
- [Proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md)

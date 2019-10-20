---
title: 'Nasıl yapılır: birden çok platformu hedeflemek için projeleri yapılandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bb759faff99b641f24df87f73bc1d3d52b6635cc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663554"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Nasıl Yapılır: Projeleri Hedef Birden Çok Platform İçin Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bir çözümün birçok farklı CPU mimarilerini veya platformunu aynı anda hedeflemesi için bir yol sağlar. Bunlara ayarlanacak özelliklere **Configuration Manager** iletişim kutusu üzerinden erişilir.

## <a name="targeting-a-platform"></a>Platformu hedefleme
 **Configuration Manager** iletişim kutusu, çözüm düzeyi ve proje düzeyi yapılandırma ve platform oluşturmanıza ve ayarlamanıza olanak sağlar. Çözüm düzeyindeki yapılandırmaların ve hedeflerin her birleşimi onunla ilişkili benzersiz bir özellikler kümesine sahip olabilir ve örneğin, bir [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] platformunu hedefleyen bir yayın yapılandırması olan bir yayın yapılandırması olan bir sürüm yapılandırması arasında kolayca geçiş yapabilirsiniz. x86 platformunu ve bir x86 platformunu hedefleyen bir hata ayıklama yapılandırmasını hedefler.

#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Yapılandırmanızı farklı bir platformu hedefleyecek şekilde ayarlamak için

1. **Yapı** menüsünde **Configuration Manager**' a tıklayın.

2. **Etkin çözüm platformu kutusunda**çözümünüzün hedeflemesini istediğiniz platformu seçin veya yeni bir platform oluşturmak için **\<New >** seçin. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], uygulamanızı, **Configuration Manager** iletişim kutusunda etkin platform olarak ayarlanan platformu hedefleyecek şekilde derler.

## <a name="removing-a-platform"></a>Platformu kaldırma
 Platforma ihtiyacınız olmadığını fark ederseniz Configuration Manager iletişim kutusunu kullanarak kaldırabilirsiniz. Bu, yapılandırma ve hedefin bu birleşimi için yapılandırdığınız tüm çözümü ve proje ayarlarını kaldırır.

#### <a name="to-remove-a-platform"></a>Bir platformu kaldırmak için

1. **Yapı** menüsünde **Configuration Manager**' a tıklayın.

2. **Etkin çözüm platformu kutusunda** **\<Edit >** ' ni seçin. **Çözüm platformlarını Düzenle** iletişim kutusu açılır.

3. Kaldırmak istediğiniz platforma tıklayın ve **Kaldır**' a tıklayın.

## <a name="targeting-multiple-platforms-with-one-solution"></a>Birden çok platformu tek bir çözümle hedefleme
 Ayarları yapılandırma ve platform ayarlarının birleşimine göre değiştirebildiğinden, birden fazla platformu hedefleyebilir bir çözüm ayarlayabilirsiniz.

#### <a name="to-target-multiple-platforms"></a>Birden çok platformu hedeflemek için

1. Çözüm için en az iki hedef platform eklemek için **Configuration Manager** kullanın.

2. **Etkin çözüm platformu** listesinden hedeflemek istediğiniz platformu seçin.

3. Çözümü oluşturun.

#### <a name="to-build-multiple-solution-configurations-at-once"></a>Aynı anda birden çok çözüm yapılandırması oluşturmak için

1. Çözüm için en az iki hedef platform eklemek için **Configuration Manager** kullanın.

2. Aynı anda birkaç çözüm yapılandırması oluşturmak için **Batch derleme** penceresini kullanın.

   Bir çözüm düzeyi platformun (örneğin, [!INCLUDE[vcprx64](../includes/vcprx64-md.md)]) ve bu çözüm içinde aynı platformu hedefleyen hiçbir proje olmaması mümkündür. Çözümünüzde, her biri farklı platformları hedefleyen birden çok projenin olması da mümkündür. Bu durumlardan birine sahipseniz, karışıklığı önlemek için açıklayıcı bir adla yeni bir yapılandırma oluşturmanız önerilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md) [derleme yapılandırmalarının](../ide/understanding-build-configurations.md) [Visual Studio 'da proje ve çözüm oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)

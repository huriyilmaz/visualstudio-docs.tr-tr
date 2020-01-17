---
title: 'Nasıl yapılır: birden çok platformu hedeflemek için projeleri yapılandırma'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b86a5c95131a4dcb2e6af199b57e9c8302790b5
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114456"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Nasıl yapılır: birden çok platformu hedeflemek için projeleri yapılandırma

Visual Studio, bir çözümün birçok farklı CPU mimarilerini veya platformunu aynı anda hedeflemesi için bir yol sağlar. Bunlara ayarlanacak özelliklere **Configuration Manager** iletişim kutusu üzerinden erişilir.

## <a name="target-a-platform"></a>Bir platformu hedefleyin

**Configuration Manager** iletişim kutusu, çözüm düzeyi ve proje düzeyi yapılandırma ve platform oluşturmanıza ve ayarlamanıza olanak sağlar. Çözüm düzeyindeki yapılandırmaların ve hedeflerin her birleşimi kendisiyle ilişkili benzersiz bir özellikler kümesine sahip olabilir. Örneğin, bir [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] platformunu hedefleyen bir yayın yapılandırması, x86 platformunu hedefleyen bir sürüm yapılandırması ve x86 platformunu hedefleyen bir hata ayıklama yapılandırması arasında kolayca geçiş yapabilirsiniz.

1. **Yapı** menüsünde, **Yapılandırma Yöneticisi**’ne tıklayın.

2. **Etkin çözüm platformu kutusunda**çözümünüzün hedeflemesini istediğiniz platformu seçin veya yeni bir platform oluşturmak için **Yeni\<** seçin. Visual Studio, **Configuration Manager** iletişim kutusunda etkin platform olarak ayarlanan platformu hedeflemek için uygulamanızı derler.

## <a name="remove-a-platform"></a>Platformu kaldırma

Platforma ihtiyacınız olmadığını fark ederseniz **Configuration Manager** iletişim kutusunu kullanarak kaldırabilirsiniz. Bu, yapılandırma ve hedefin bu birleşimi için yapılandırdığınız tüm çözümü ve proje ayarlarını kaldırır.

1. **Yapı** menüsünde, **Yapılandırma Yöneticisi**’ne tıklayın.

2. **Etkin çözüm platformu kutusunda** **\<Düzenle >** ' yi seçin. **Çözüm platformlarını Düzenle** iletişim kutusu açılır.

3. Kaldırmak istediğiniz platforma tıklayın ve **Kaldır**' a tıklayın.

## <a name="target-multiple-platforms-with-one-solution"></a>Birden çok platformu tek bir çözümle hedefleme

Ayarları yapılandırma ve platform ayarlarının birleşimine göre değiştirebildiğinden, birden fazla platformu hedefleyebilir bir çözüm ayarlayabilirsiniz.

### <a name="to-target-multiple-platforms"></a>Birden çok platformu hedeflemek için

1. Çözüm için en az iki hedef platform eklemek için **Configuration Manager** kullanın.

2. **Etkin çözüm platformu** listesinden hedeflemek istediğiniz platformu seçin.

3. Çözümü oluşturun.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Aynı anda birden çok çözüm yapılandırması oluşturmak için

1. Çözüm için en az iki hedef platform eklemek için **Configuration Manager** kullanın.

2. Aynı anda birkaç çözüm yapılandırması oluşturmak için **Batch derleme** penceresini kullanın.

   Bir çözüm düzeyi platformun (örneğin, [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]) ve bu çözüm içinde aynı platformu hedefleyen hiçbir proje olmaması mümkündür. Çözümünüzde, her biri farklı platformları hedefleyen birden çok projenin olması da mümkündür. Bu durumlardan birine sahipseniz, karışıklığı önlemek için açıklayıcı bir adla yeni bir yapılandırma oluşturmanız önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)

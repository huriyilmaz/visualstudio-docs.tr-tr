---
title: 'Nasıl yapılır: birden çok platformu hedeflemek için projeleri yapılandırma'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0618d571258817b5e9653a38a7801c2e4d14e687
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284574"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Nasıl yapılır: birden çok platformu hedeflemek için projeleri yapılandırma

Visual Studio, bir çözümün birçok farklı CPU mimarilerini veya platformunu aynı anda hedeflemesi için bir yol sağlar. Bunlara ayarlanacak özelliklere **Configuration Manager** iletişim kutusu üzerinden erişilir.

## <a name="target-a-platform"></a>Bir platformu hedefleyin

**Configuration Manager** iletişim kutusu, çözüm düzeyi ve proje düzeyi yapılandırma ve platform oluşturmanıza ve ayarlamanıza olanak sağlar. Çözüm düzeyindeki yapılandırmaların ve hedeflerin her birleşimi kendisiyle ilişkili benzersiz bir özellikler kümesine sahip olabilir. Örneğin, platformu hedefleyen bir yayın yapılandırması [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] , x86 platformunu hedefleyen bir sürüm yapılandırması ve x86 platformunu hedefleyen bir hata ayıklama yapılandırması arasında kolayca geçiş yapabilirsiniz.

1. **Yapı** menüsünde, **Yapılandırma Yöneticisi**’ne tıklayın.

2. **Etkin çözüm platformu kutusunda**çözümünüzün hedeflemesini istediğiniz platformu seçin veya **\<New>** Yeni bir platform oluşturmayı seçin. Visual Studio, **Configuration Manager** iletişim kutusunda etkin platform olarak ayarlanan platformu hedeflemek için uygulamanızı derler.

## <a name="remove-a-platform"></a>Platformu kaldırma

Platforma ihtiyacınız olmadığını fark ederseniz **Configuration Manager** iletişim kutusunu kullanarak kaldırabilirsiniz. Bu, yapılandırma ve hedefin bu birleşimi için yapılandırdığınız tüm çözümü ve proje ayarlarını kaldırır.

1. **Yapı** menüsünde, **Yapılandırma Yöneticisi**’ne tıklayın.

2. **Etkin çözüm platformu kutusunda**öğesini seçin **\<Edit>** . **Çözüm platformlarını Düzenle** iletişim kutusu açılır.

3. Kaldırmak istediğiniz platforma tıklayın ve **Kaldır**' a tıklayın.

## <a name="target-multiple-platforms-with-one-solution"></a>Birden çok platformu tek bir çözümle hedefleme

Ayarları yapılandırma ve platform ayarlarının birleşimine göre değiştirebildiğinden, birden fazla platformu hedefleyebilir bir çözüm ayarlayabilirsiniz.

### <a name="to-target-multiple-platforms"></a>Birden çok platformu hedeflemek için

1. Çözüm için en az iki hedef platform eklemek için **Configuration Manager** kullanın.

2. **Etkin çözüm platformu** listesinden hedeflemek istediğiniz platformu seçin.

3. Çözümü derleyin.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Aynı anda birden çok çözüm yapılandırması oluşturmak için

1. Çözüm için en az iki hedef platform eklemek için **Configuration Manager** kullanın.

2. Aynı anda birkaç çözüm yapılandırması oluşturmak için **Batch derleme** penceresini kullanın.

   Bir çözüm düzeyi platformun, örneğin,, [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] ve bu çözüm içinde aynı platformu hedefleyen hiçbir projesi yok olarak ayarlanmış olması mümkündür. Çözümünüzde, her biri farklı platformları hedefleyen birden çok projenin olması da mümkündür. Bu durumlardan birine sahipseniz, karışıklığı önlemek için açıklayıcı bir adla yeni bir yapılandırma oluşturmanız önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)

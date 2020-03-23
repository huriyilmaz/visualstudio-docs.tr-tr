---
title: 'Nasıl yapilir: Projeleri birden çok platformu hedefleecek şekilde yapılandırma'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114456"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Nasıl yapilir: Projeleri birden çok platformu hedefleecek şekilde yapılandırma

Visual Studio, aynı anda birkaç farklı CPU mimarisini veya platformlarını hedefleyen bir çözüm sağlar. Bunları ayarlayabilmek için Configuration **Manager** iletişim kutusundan erişilir.

## <a name="target-a-platform"></a>Bir platformu hedefle

**Configuration Manager** iletişim kutusu, çözüm düzeyi ve proje düzeyinde yapılandırmalar ve platformlar oluşturmanıza ve ayarlamanıza olanak tanır. Çözüm düzeyindeki yapılandırmaların ve hedeflerin her birleşimi, örneğin bir [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] platformu hedefleyen bir sürüm yapılandırması, x86 platformlarını hedefleyen bir sürüm yapılandırması ve x86 platform'u hedefleyen hata ayıklama yapılandırması arasında kolayca geçiş yapabilirsiniz.

1. **Yapı** menüsünde, **Yapılandırma Yöneticisi**’ne tıklayın.

2. Etkin **çözüm platformu kutusunda,** çözümünüzü hedeflemek istediğiniz platformu seçin veya yeni bir platform oluşturmak için ** \<New>'ı** seçin. Visual Studio, **Configuration Manager** iletişim kutusunda etkin platform olarak ayarlanan platformu hedeflemek için uygulamanızı derleyecek.

## <a name="remove-a-platform"></a>Bir platformu kaldırma

Bir platforma ihtiyacınız olmadığını fark ederseniz, **Configuration Manager** iletişim kutusunu kullanarak platformu kaldırabilirsiniz. Bu, yapılandırma ve hedef in birleşimi için yapılandırdığınız tüm çözüm ve proje ayarlarını kaldırır.

1. **Yapı** menüsünde, **Yapılandırma Yöneticisi**’ne tıklayın.

2. Etkin **çözüm platformu kutusunda,** ** \<>Edit'i **seçin. **Çözüm Platformlarını Edit** iletişim kutusu açılır.

3. Kaldırmak istediğiniz platformu tıklatın ve **Kaldır'ı**tıklatın.

## <a name="target-multiple-platforms-with-one-solution"></a>Tek bir çözümle birden fazla platformu hedefle

Ayarları yapılandırma ve platform ayarlarının birleşimine göre değiştirebileceğinizden, birden fazla platformu hedeflenebilen bir çözüm ayarlayabilirsiniz.

### <a name="to-target-multiple-platforms"></a>Birden çok platformu hedeflemek için

1. Çözüm için en az iki hedef platform eklemek için **Configuration Manager'ı** kullanın.

2. **Etkin çözüm platformu** listesinden hedeflemek istediğiniz platformu seçin.

3. Çözümü derleyin.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Aynı anda birden çok çözüm yapılandırması oluşturmak için

1. Çözüm için en az iki hedef platform eklemek için **Configuration Manager'ı** kullanın.

2. Aynı anda birden çok çözüm yapılandırması oluşturmak için **Toplu İş Oluşturma** penceresini kullanın.

   Örneğin, [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]çözüm düzeyinde bir platform ayarı yapmak ve bu çözüm içinde aynı platformu hedefleyen hiçbir projeye sahip olmak mümkündür. Çözümünüzde her biri farklı platformları hedefleyen birden fazla proje de olması mümkündür. Bu durumlardan birine sahipseniz, karışıklığı önlemek için açıklayıcı bir ada sahip yeni bir yapılandırma oluşturmanız önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılı: Yapılandırmalar oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)
- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Visual Studio'da projeler ve çözümler oluşturun ve temizleyin](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)

---
title: Karışık modda hata ayıkla | Microsoft Docs
description: Çağıran uygulamanın projesinin özellik sayfalarında karışık modda hata ayıklamayı (yönetilen ve yerel kod birlikte) nasıl etkinleştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0e25cd55efbd7d686a8251b2fb6da399e4977e50
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105242"
---
# <a name="how-to-debug-in-mixed-mode-c-c-visual-basic"></a>Nasıl yapılır: karışık modda hata ayıklama (C#, C++, Visual Basic)

Aşağıdaki yordamlarda, karışık modda hata ayıklama olarak da bilinen yönetilen ve yerel kod için hata ayıklamanın nasıl etkinleştirileceği açıklanır. İki karışık mod hata ayıklama senaryosu vardır:

- DLL 'yi çağıran uygulama yerel kodda yazılır ve DLL yönetilir.

- DLL 'yi çağıran uygulama yönetilen kodda yazılır ve DLL yerel koddur. Bu senaryoda daha ayrıntılı bilgi için izlenecek bir öğretici için bkz. [yönetilen ve yerel kodda hata ayıklama](../debugger/how-to-debug-managed-and-native-code.md).

Çağıran uygulama projesinin **özellik** sayfalarında hem yönetilen hem de yerel hata ayıklayıcıları etkinleştirebilirsiniz. Ayarlar, yerel ve yönetilen uygulamalar arasında farklılık gösterir.

Çağıran bir uygulamanın projesine erişiminiz yoksa dll 'de dll projesinden hata ayıklaması yapabilirsiniz. Yalnızca DLL projesinde hata ayıklamak için karışık moda ihtiyacınız yoktur. Daha fazla bilgi için bkz. [nasıl yapılır: DLL projesinde hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md).

> [!NOTE]
> gördüğünüz iletişim kutuları ve komutlar, Visual Studio ayarlarınıza veya sürümüne bağlı olarak bu makaledeki olanlarından farklı bir şekilde farklılık gösterebilir. ayarlarınızı değiştirmek için **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar**' ı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Yerel bir çağıran uygulama için karışık modda hata ayıklamayı etkinleştir

1. **Çözüm Gezgini** ' de C++ projesini seçin ve **Özellikler** simgesine tıklayın, **alt** + **ENTER** tuşuna basın veya sağ tıklayıp **Özellikler**' i seçin.

1. **\<Project> Özellik sayfaları** Iletişim kutusunda, **yapılandırma özellikleri**' ni genişletin ve ardından **hata ayıklama**' yı seçin.

1. **Hata ayıklayıcı türünü** **karışık** veya **Otomatik** olarak ayarlayın.

1. **Tamam**’ı seçin.

   ![Karışık modda hata ayıklamayı etkinleştir](../debugger/media/dbg-mixed-mode-from-native.png "Karışık modda hata ayıklamayı etkinleştir")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Yönetilen bir çağıran uygulama için karışık modda hata ayıklamayı etkinleştir

1. **Çözüm Gezgini** ' de C# veya Visual Basic projesi seçin ve **özellikler** simgesini seçin, **Alt** + **enter** tuşuna basın veya sağ tıklayıp **özellikler**' i seçin.

1. **Hata Ayıkla** sekmesini seçin ve ardından **yerel kod hata ayıklamayı etkinleştir**' i seçin.

1. Değişiklikleri kaydetmek için Özellikler sayfasını kapatın.

   ![Yerel kod hata ayıklamasını etkinleştir](../debugger/media/dbg-mixed-mode-from-csharp.png "Yerel kod hata ayıklamasını etkinleştir")

> [!NOTE]
> Visual Studio 2017 ' den başlayarak Visual Studio çoğu sürümünde, .net Core uygulamasında yerel kod için karışık modda hata ayıklamayı etkinleştirmek amacıyla proje özellikleri yerine *launchSettings.js* dosyasında kullanmanız gerekir. Ayrıntılar için bkz. [yönetilen ve yerel kodda hata ayıklama](../debugger/how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: DLL Projesinde hata ayıklama](../debugger/how-to-debug-from-a-dll-project.md)
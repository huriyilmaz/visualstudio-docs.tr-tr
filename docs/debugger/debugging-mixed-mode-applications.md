---
title: Mixed-Mode Applications | Microsoft Docs
description: Yerel kodu ortak dil çalışma zamanı üzerinde çalışan yönetilen kodla birleştiren bir uygulama olan karma modlu uygulamanın hata ayıklaması Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 13eff8e5d1d078c838d0b193dc5fe7b88a23f56b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097486"
---
# <a name="debugging-mixed-mode-applications"></a>Karışık Mod Uygulamalarında Hata Ayıklama
Bir karma mod uygulaması yerel kod (C++)'yı yönetilen kodla (örneğin, Visual Basic, Visual C# veya ortak dil çalışma zamanında çalışan C++) bir araya getiren herhangi bir uygulamadır. Karma mod uygulamalarında hata ayıklama büyük ölçüde saydamdır; tek mod uygulamanın hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayıklaması çok farklı değildir. Ancak birkaç özel nokta vardır.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>C++ Düzenlemeyi Etkinleştir ve Karma Mod Hata Ayıklamaya Devam Et

C++ için Düzenle ve Devam'ı etkinleştirmek için [bkz. Düzenle ve Devam'ı etkinleştirme ve devre dışı bırakma.](../debugger/how-to-enable-and-disable-edit-and-continue.md)

> [!NOTE]
> Visual Studio 2013'de C++ için Düzenle ve Devam Et'i kullanmak için eski hata ayıklama alt yapısına dönmeniz gerekir. Microsoft [Uygulama Yaşam Döngüsü Yönetimi](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/) blog Visual Studio 2013'da Yönetilen Uyumluluk Moduna Geçme makalesi'ne bakın.

## <a name="property-evaluation-in-mixed-mode-applications"></a>Karma Mod Uygulamalarında Özellik Değerlendirme
 Karma modlu bir uygulamada, hata ayıklayıcı tarafından özelliklerin değerlendirilmesi maliyetli bir işlemdir. Sonuç olarak, atlama gibi hata ayıklama işlemleri yavaşlamaya neden olabilir. Daha fazla bilgi için bkz. [Adımlama.](/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)) Karma mod hata ayıklama içinde düşük performansla karşılaşırsanız, hata ayıklayıcısını penceresindeki özellik değerlendirmesini devre dışı bırakmayı düşünebilirsiniz.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için Araçlar menüsünde İçeri ve Dışarı  **Ayarlar'yi** seçin. Daha fazla bilgi için [bkz. Ayarları sıfırlama.](../ide/environment-settings.md#reset-settings)

### <a name="to-turn-off-property-evaluation"></a>Özellik değerlendirmeyi devre dışı bırakmak için

1. Araçlar menüsünde **Seçenekler'i** **seçin.**

2. Seçenekler **iletişim** kutusunda Hata ayıklama klasörünü **açın** ve Genel **kategorisini** seçin.

3. Özellik **değerlendirmesini ve diğer örtülü işlev çağrılarını etkinleştir onay kutusunun** işaretini kaldırın.

   Yerel çağrı yığınları ve yönetilen çağrı yığınları farklı olduğundan, hata ayıklayıcı karma kod için tam çağrı yığınını her zaman sağlayamaz. Yerel kod yönetilen kodu çağırdığında, bazı tutarsızlıklar görebilirsiniz. Daha fazla bilgi için Çağrı [Yığını PenceresindeKi Karışık Kod ve Eksik Bilgiler'e bakın.](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
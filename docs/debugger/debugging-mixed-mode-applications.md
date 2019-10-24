---
title: Karışık modda uygulamalarda hata ayıklama | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c245b6c56b7480a9395394d707aa0f02fb22fc9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738188"
---
# <a name="debugging-mixed-mode-applications"></a>Karışık Mod Uygulamalarında Hata Ayıklama
Bir karma mod uygulaması yerel kod (C++)'yı yönetilen kodla (örneğin, Visual Basic, Visual C# veya ortak dil çalışma zamanında çalışan C++) bir araya getiren herhangi bir uygulamadır. Karma mod uygulamalarının hata ayıklaması büyük ölçüde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] içinde saydamdır; Tek modlu bir uygulamada hata ayıklamanın çok farklı olması. Ancak birkaç özel nokta vardır.

## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>C++ Düzenlemeyi Etkinleştir ve Karma Mod Hata Ayıklamaya Devam Et

Düzenle ve devam et özelliğini etkinleştirmek C++için, bkz. Düzenle ve devam et 'i [etkinleştirme ve devre dışı bırakma](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Visual Studio 2013'de C++ için Düzenle ve Devam Et'i kullanmak için eski hata ayıklama alt yapısına dönmeniz gerekir. Bkz. Microsoft uygulama yaşam döngüsü yönetimi blogu 'nda [Visual Studio 2013 yönetilen uyumluluk moduna geçme](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/) .

## <a name="property-evaluation-in-mixed-mode-applications"></a>Karma Mod Uygulamalarında Özellik Değerlendirme
 Karma modlu bir uygulamada, hata ayıklayıcı tarafından özelliklerin değerlendirilmesi maliyetli bir işlemdir. Sonuç olarak, atlama gibi hata ayıklama işlemleri yavaşlamaya neden olabilir. Daha fazla bilgi için bkz. [Adımlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ek13f001(v=vs.100)). Karma mod hata ayıklama içinde düşük performansla karşılaşırsanız, hata ayıklayıcısını penceresindeki özellik değerlendirmesini devre dışı bırakmayı düşünebilirsiniz.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

### <a name="to-turn-off-property-evaluation"></a>Özellik değerlendirmeyi devre dışı bırakmak için

1. **Araçlar** menüsünde **Seçenekler**' i seçin.

2. **Seçenekler** iletişim kutusunda, **hata ayıklama** klasörünü açın ve **genel** kategorisini seçin.

3. **Özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir** onay kutusunu temizleyin.

   Yerel çağrı yığınları ve yönetilen çağrı yığınları farklı olduğundan, hata ayıklayıcı karma kod için tam çağrı yığınını her zaman sağlayamaz. Yerel kod yönetilen kodu çağırdığında, bazı tutarsızlıklar görebilirsiniz. Daha fazla bilgi için bkz. [çağrı yığını penceresinde karışık kod ve eksik bilgiler](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
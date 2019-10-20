---
title: Windows Forms uygulamaları tasarlama
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26ad18da19d5a2e53199b49e7acc024c728be9c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634024"
---
# <a name="windows-forms-designer-overview"></a>Windows Form Tasarımcısı’na genel bakış

Visual Studio 'daki Windows Form Tasarımcısı, Windows Forms tabanlı uygulamalar oluşturmak için hızlı bir geliştirme çözümü sağlar. Windows Form Tasarımcısı, forma kolayca denetim eklemenizi, bunları düzenlemenizi ve olayları için kod yazmanızı sağlar. Windows Forms hakkında daha fazla bilgi için bkz. [Windows Forms genel bakış](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>İşlevi

Tasarımcı kullanarak şunları yapabilirsiniz:

- Form için bileşenleri, veri denetimlerini veya Windows tabanlı denetimleri ekleyin.

- Tasarımcıda forma çift tıklayın ve bu form için `Load` olayına kod yazın veya formdaki bir denetime çift tıklayın ve denetimin varsayılan olayı için kodu yazın.

- Denetimi seçip bir ad yazarak bir denetimin metin özelliğini düzenleyin.

- Seçili denetimin yerleşimini fareyle veya ok tuşlarıyla taşıyarak ayarlayın. Benzer şekilde, CTRL ve ok tuşlarını kullanarak yerleşimi daha kesin bir şekilde ayarlayın. Son olarak, Shift ve ok tuşlarını kullanarak denetimin boyutunu ayarlayın.

- Tıklatırken **SHIFT** veya **CTRL** ' i seçerek birden çok denetim seçin. SHIFT + tıklama **tuşlarını**kullanırken, seçilen ilk denetim, boyutu hizalarken veya düzenleme yaparken baskın denetimdir. **CTRL**+ tıklama kullanılırken, seçilen son denetim baskın olduğundan, baskın denetim her yeni denetim eklenmiş şekilde değişir. Alternatif olarak, seçmek istediğiniz denetimlerin çevresine bir seçim dikdörtgeni sürükleyerek birden çok denetim seçebilirsiniz.

> [!NOTE]
> Formun kaynak ( *. resx*) dosyasında değişiklik yapmak Için kaynak düzenleyicisini değil Windows Form Tasarımcısı kullanın. Form tabanlı. resx dosyasını düzenlerseniz, kaynak düzenleyicisinde yaptığınız değişikliklerin kaybedilmesi gerektiğini belirten bir uyarı görürsünüz. Bunun nedeni Windows Form Tasarımcısı. resx dosyasını oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms genel bakış](/dotnet/framework/winforms/windows-forms-overview)
- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/)
- [Windows Forms Kullanıcı girişi](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Windows Forms veri bağlama](/dotnet/framework/winforms/windows-forms-data-binding)
- [Windows Forms uygulamalarını geliştirin](/dotnet/framework/winforms/advanced/)
- <xref:System.Windows.Forms?displayProperty=fullName> API başvurusu
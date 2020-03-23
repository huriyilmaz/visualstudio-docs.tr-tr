---
title: Windows Forms uygulamalarını tasarlayın
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 171cdffa569b342bdbc7dd0da1c8da218e1d622c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589896"
---
# <a name="windows-forms-designer-overview"></a>Windows Form Tasarımcısı’na genel bakış

Visual Studio'daki Windows Forms Designer, Windows Forms tabanlı uygulamalar oluşturmak için hızlı bir geliştirme çözümü sağlar. Windows Forms Designer, bir forma kolayca denetim eklemenize, düzenlemenize ve etkinlikleri için kod yazmanıza olanak tanır. Windows Formlar hakkında daha fazla bilgi için [Windows Formlar genel bakış](/dotnet/framework/winforms/windows-forms-overview)bilgisine bakın.

## <a name="functionality"></a>İşlev

Tasarımcıyı kullanarak şunları yapabilirsiniz:

- Bir forma bileşenler, veri denetimleri veya Windows tabanlı denetimler ekleyin.

- Bu form için tasarımcıdaki formu çift `Load` tıklatın ve bu form için kod yazın veya form üzerindeki denetimi çift tıklatın ve denetimin varsayılan olayı için kod yazın.

- Denetimi seçip bir ad yazarak denetimin Metin özelliğini düzenleme.

- Fare veya ok tuşları ile hareket ettirerek seçili denetimin yerleşimini ayarlayın. Benzer şekilde, Ctrl ve ok tuşlarını kullanarak yerleşimi daha hassas bir şekilde ayarlayın. Son olarak, Shift ve ok tuşlarını kullanarak denetimin boyutunu ayarlayın.

- Tıklatırken **Shift** veya **Ctrl'yi** seçerek birden çok denetim seçin. Sing **Shift**+click kullanırken, seçilen ilk denetim boyutu hizalarken veya değiştirirken baskın denetimdir. **Ctrl**+click kullanırken, seçilen son denetim baskındır, bu nedenle her yeni denetim eklendiğinde baskın kontrol değişir. Alternatif olarak, seçmek istediğiniz denetimlerin etrafında bir seçim dikdörtgeni sürükleyerek birden çok denetim seçebilirsiniz.

> [!NOTE]
> Formun kaynağında değişiklik yapmak için Kaynak Düzenleyicisi'ni değil, Windows Forms*Designer'ı*kullanın. Form tabanlı .resx dosyasını edinirseniz, Kaynak Düzenleyicisi'nde yaptığınız değişikliklerin kaybolabileceğine dair bir uyarı görürsünüz. Bunun nedeni, Windows Forms Designer'ın .resx dosyasını oluşturmasıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Formlarına genel bakış](/dotnet/framework/winforms/windows-forms-overview)
- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/)
- [Windows Formlarında Kullanıcı girişi](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Windows Formlarında veri bağlama](/dotnet/framework/winforms/windows-forms-data-binding)
- [Windows Forms uygulamalarını geliştirin](/dotnet/framework/winforms/advanced/)
- <xref:System.Windows.Forms?displayProperty=fullName>API başvurusu

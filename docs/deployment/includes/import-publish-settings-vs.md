---
ms.openlocfilehash: 94c2c733b631ef5e727c79a6e093bb224aec38c4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249832"
---

1. Visual Studio 'da ASP.NET projesinin açık olduğu bilgisayarda Çözüm Gezgini ' de projeye sağ tıklayın ve **Yayımla**' yı seçin.

   Daha önce herhangi bir yayımlama profili yapılandırdıysanız, **Yayımla** bölmesi görüntülenir. **Yeni** ' ye tıklayın veya **Yeni profil oluşturun**.

1. Bir profili içeri aktarma seçeneğini belirleyin.

   ::: moniker range=">=vs-2019"
   **Yayımla** Iletişim kutusunda **profili içeri aktar**' a tıklayın.
   ::: moniker-end
   ::: moniker range="vs-2017"
   **Yayımla hedefi seç** Iletişim kutusunda **profili içeri aktar**' a tıklayın.
   ::: moniker-end

   ![Yayımla ' yı seçin](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Önceki bölümde oluşturduğunuz yayımlama ayarları dosyasının konumuna gidin.

1. **Yayımlama ayarları dosyasını Içeri aktar** iletişim kutusunda, öğesine gidin ve önceki bölümde oluşturduğunuz profili seçin ve **Aç**' a tıklayın.

   ::: moniker range=">=vs-2019"
   Yayımlama profilini kaydetmek için **son** ' a tıklayın ve ardından **Yayımla**' ya tıklayın.

   Visual Studio dağıtım işlemini başlatır ve çıkış penceresinde ilerleme ve sonuçlar gösterilir.

   Herhangi bir dağıtım hatası alırsanız ayarları düzenlemek için **Düzenle** ' ye tıklayın. Ayarları değiştirin ve yeni ayarları test etmek için **Doğrula** ' ya tıklayın. Ana bilgisayar adı bulunamazsa **sunucu** ve **hedef URL** alanlarında ana bilgisayar adı yerine IP adresini deneyin.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio dağıtım işlemini başlatır ve çıkış penceresinde ilerleme ve sonuçlar gösterilir.

   Herhangi bir dağıtım hatası alırsanız ayarları düzenlemek için **Ayarlar** ' a tıklayın. Ayarları değiştirin ve yeni ayarları test etmek için **Doğrula** ' ya tıklayın. Ana bilgisayar adı bulunamazsa **sunucu** ve **hedef URL** alanlarında ana bilgisayar adı yerine IP adresini deneyin.
   ::: moniker-end

   ![Yayımla aracında Ayarları Düzenle](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)

---
title: Uzantıyı güncelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0d1464cdd2be79cd93a3e98bcf8769e8f4b8b89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837252"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Nasıl Yapılır: Bir Visual Studio Uzantısını Güncelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Güncelleştirilmiş sürümü yüklemek için **uzantıları ve güncelleştirmeleri** kullanarak sisteminizdeki bir Visual Studio uzantısını güncelleştirebilirsiniz. Bir uzantının güncelleştirilmiş bir sürümünü oluşturursanız VSıX bildirimindeki sürüm numarasını artırarak onu güncelleştirilmiş olarak belirtebilirsiniz.

 Gelen uzantının VSıX bildirimi `ID` yüklü bir ve daha yüksek bir sayıyla aynı olduğunda güncelleştirmeler yüklenir `Version` . `Version`Numara aynı veya daha düşükse, paket yüklenemez. `ID`Değerler eşleşmezse, henüz yüklenmeyen paket ayrı bir uzantı olarak tanınır.

 Geliştirme sırasında çakışmaların önlenmesine yardımcı olmak için, devam eden uzantıların önceki sürümlerini kaldırmanızı ve ayrıca diğer olası çakışan uzantıları kaldırmanızı veya devre dışı bırakmanızı öneririz.

### <a name="to-update-an-extension-on-your-system"></a>Sisteminizdeki bir uzantıyı güncelleştirmek için

1. **Araçlar** menüsünde **Uzantılar ve Güncelleştirmeler**’e tıklayın.

2. Sol bölmede **güncelleştirmeler**' e tıklayın.

3. Orta bölmede, yüklemek istediğiniz güncelleştirmeye tıklayın.

     Güncelleştirilmiş uzantının sürüm numarası sağ bölmede diğer bilgilerle birlikte görüntülenir.

4. Sağ bölmenin alt kısmındaki **Güncelleştir**' e tıklayın.

### <a name="to-publish-an-update-of-an-extension"></a>Bir uzantının güncelleştirmesini yayımlamak için

1. Visual Studio 'da, güncelleştirmek istediğiniz uzantının çözümünü açın. Değişiklikleri yapın.

    > [!IMPORTANT]
    > İmzasız tüm Kullanıcı uzantıları otomatik olarak güncellenmez. Uzantılarınızı her zaman imzalamanız gerekir.

2. **Çözüm Gezgini**' de, kaynak. uzantı. manifest ' i açın.

3. Bildirim tasarımcısında, **Sürüm** alanındaki sayının değerini artırın.

4. Çözümü kaydedin ve derleyin.

5. Yeni. vsix dosyasını (projenin \bin\Debug\ klasöründe) [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesine yükleyin.

     Uzantının önceki bir sürümüne sahip olan bir Kullanıcı **uzantıları ve güncelleştirmeleri**açtığında yeni sürüm **güncelleştirmeler** listesinde görünür ve araç, güncelleştirmeleri otomatik olarak aramak üzere ayarlanır.

     **Güncelleştirmeler bölmesinin alt** kısmındaki güncelleştirmeler için otomatik denetlemeyi etkinleştirebilir veya devre dışı bırakabilirsiniz (**kullanılabilir güncelleştirmelerin otomatik algılanmasını etkinleştir/devre dışı bırak**), **Araçlar/Seçenekler/ortam/Uzantılar ve güncelleştirmeler**'deki **güncelleştirme denetimi** ayarını değiştirir.

    > [!NOTE]
    > Visual Studio 2015 güncelleştirme 2 ' den başlayarak, Kullanıcı başına uzantılar, tüm Kullanıcı Uzantıları veya her ikisi için de otomatik güncelleştirme isteyip istemediğinizi ( **Araçlar/Seçenekler/ortam/Uzantılar ve güncelleştirmeler**içinde) belirtebilirsiniz (varsayılan ayar).

## <a name="see-also"></a>Ayrıca Bkz.
 [VSIX paketinin anatomi](../extensibility/anatomy-of-a-vsix-package.md) [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)

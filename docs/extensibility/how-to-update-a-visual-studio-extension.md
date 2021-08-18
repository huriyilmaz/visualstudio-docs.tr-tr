---
title: 'nasıl yapılır: Visual Studio uzantısını güncelleştirme | Microsoft Docs'
description: güncelleştirilmiş sürümü yüklemek için uzantıları ve güncelleştirmeleri kullanarak sisteminizdeki Visual Studio uzantısını güncelleştirme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c69ab2bedfda4394c0256db7040de39e8a520ca4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124821"
---
# <a name="how-to-update-a-visual-studio-extension"></a>nasıl yapılır: Visual Studio uzantısını güncelleştirme
güncelleştirilmiş sürümü yüklemek için **uzantıları ve güncelleştirmeleri** kullanarak sisteminizdeki Visual Studio uzantısını güncelleştirebilirsiniz. Bir uzantının güncelleştirilmiş bir sürümünü oluşturursanız VSıX bildirimindeki sürüm numarasını artırarak onu güncelleştirilmiş olarak belirtebilirsiniz.

 Gelen uzantının VSıX bildirimi `ID` yüklü bir ve daha yüksek bir sayıyla aynı olduğunda güncelleştirmeler yüklenir `Version` . `Version`Numara aynı veya daha düşükse, paket yüklenemez. `ID`Değerler eşleşmezse, henüz yüklenmeyen paket ayrı bir uzantı olarak tanınır.

 Geliştirme sırasında çakışmaların önlenmesine yardımcı olmak için, devam eden uzantıların önceki sürümlerini kaldırmanızı ve ayrıca diğer olası çakışan uzantıları kaldırmanızı veya devre dışı bırakmanızı öneririz.

## <a name="to-update-an-extension-on-your-system"></a>Sisteminizdeki bir uzantıyı güncelleştirmek için

1. **Araçlar** menüsünde **Uzantılar ve Güncelleştirmeler**’e tıklayın.

2. Sol bölmede **güncelleştirmeler**' e tıklayın.

3. Orta bölmede, yüklemek istediğiniz güncelleştirmeye tıklayın.

     Güncelleştirilmiş uzantının sürüm numarası sağ bölmede diğer bilgilerle birlikte görüntülenir.

4. Sağ bölmenin alt kısmındaki **Güncelleştir**' e tıklayın.

## <a name="to-publish-an-update-of-an-extension"></a>Bir uzantının güncelleştirmesini yayımlamak için

1. Visual Studio, güncelleştirmek istediğiniz uzantının çözümünü açın. Değişiklikleri yapın.

    > [!IMPORTANT]
    > İmzasız tüm Kullanıcı uzantıları otomatik olarak güncellenmez. Uzantılarınızı her zaman imzalamanız gerekir.

2. **Çözüm Gezgini**' de, *kaynak. uzantı. manifest*' i açın.

3. Bildirim tasarımcısında, **Sürüm** alanındaki sayının değerini artırın.

4. Çözümü kaydedin ve derleyin.

5. yeni *. vsix* dosyasını (projenin * \bin\debug \* klasöründe) [Visual Studio market](https://marketplace.visualstudio.com/vs) Web sitesine Upload.

     Uzantının önceki bir sürümüne sahip olan bir Kullanıcı **uzantıları ve güncelleştirmeleri** açtığında yeni sürüm **güncelleştirmeler** listesinde görünür ve araç, güncelleştirmeleri otomatik olarak aramak üzere ayarlanır.

     **Güncelleştirmeler bölmesinin alt** kısmındaki güncelleştirmeler için otomatik denetlemeyi etkinleştirebilir veya devre dışı bırakabilirsiniz (**kullanılabilir güncelleştirmelerin otomatik algılanmasını etkinleştir/devre dışı bırak**), bu, **Araçlar**   >  **Seçenekler**  >  **ortam**  >  **uzantıları ve güncelleştirmeler**'deki güncelleştirme denetimi ayarını değiştirir.

    > [!NOTE]
    > Visual Studio 2015 güncelleştirme 2 ' den başlayarak,   >    >    >  kullanıcı başına uzantılar, tüm kullanıcı uzantıları veya her ikisi için de otomatik güncelleştirme isteyip istemediğinizi (araçlar seçenekler ortam **uzantıları ve güncelleştirmeler**' de) belirtebilirsiniz (varsayılan ayar).

## <a name="see-also"></a>Ayrıca bkz.
- [VSıX paketinin anatomumu](../extensibility/anatomy-of-a-vsix-package.md)
- [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)

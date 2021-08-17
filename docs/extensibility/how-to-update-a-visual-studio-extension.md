---
title: 'Nasıl Visual Studio: Visual Studio Uzantısını | Microsoft Docs'
description: Güncelleştirilmiş sürümü yüklemek için Visual Studio ve Güncelleştirmeler'i kullanarak sisteminize bir uzantıyı güncelleştirme hakkında bilgi alın.
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
ms.openlocfilehash: 8b1dce6d9f8e410f4cf0b642a2f50eeb864a0d54d7fedafa3a524e76615ebb83
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401602"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Nasıl Visual Studio: Visual Studio güncelleştirme
Güncelleştirilmiş sürümü yüklemek Visual Studio ve Güncelleştirmeler'i kullanarak sisteminize bir **uzantıyı** güncelleştirin. Bir uzantının güncelleştirilmiş bir sürümünü oluşturmanız halinde, VSIX bildiriminde sürüm numarasını artırarak uzantıyı güncelleştirilmiş olarak belirtemezsiniz.

 Gelen uzantının VSIX bildirimi yüklü olanla aynı ve daha yüksek bir `ID` sayıya sahip olduğunda güncelleştirmeler `Version` yüklenir. Sayı `Version` aynı veya daha düşükse paket yük olamaz. Değerler `ID` eşleşmezse, henüz yüklenmemiş paket ayrı bir uzantı olarak tanınır.

 Geliştirme sırasında çakışmaları önlemeye yardımcı olmak için devam eden uzantıların önceki sürümlerini kaldırmanızı ve ayrıca çakışan diğer uzantıları kaldırmanızı veya devre dışı bırakmanızı öneririz.

## <a name="to-update-an-extension-on-your-system"></a>Sisteminiz üzerinde bir uzantıyı güncelleştirmek için

1. **Araçlar** menüsünde **Uzantılar ve Güncelleştirmeler**’e tıklayın.

2. Sol bölmede Güncelleştirmeler'e **tıklayın.**

3. Orta bölmede, yüklemek istediğiniz güncelleştirmeye tıklayın.

     Güncelleştirilmiş uzantının sürüm numarası, diğer bilgilerle birlikte sağ bölmede görüntülenir.

4. Sağ bölmenin alt kısmında Güncelleştir'e **tıklayın.**

## <a name="to-publish-an-update-of-an-extension"></a>Uzantı güncelleştirmesini yayımlamak için

1. Bu Visual Studio güncelleştirmek istediğiniz uzantının çözümünü açın. Değişiklikleri yapın.

    > [!IMPORTANT]
    > Imzasız tüm kullanıcı uzantıları otomatik olarak güncelleştirilmez. Uzantılarınızı her zaman imzalamanız gerekir.

2. içinde **Çözüm Gezgini** *source.extension.manifest 'i açın.*

3. Bildirim tasarımcısında Sürüm alanında sayanın **değerini** artır.

4. Çözümü kaydedin ve derlemek.

5. Upload *.vsix* dosyasını (projenin *\bin\Debug \* klasöründe) [Visual Studio Market](https://marketplace.visualstudio.com/vs) Web sitesine kopyalayın.

     Uzantının önceki bir sürümüne sahip olan bir kullanıcı Uzantılar ve Güncelleştirmeler'i açtığında, aracın güncelleştirmeleri otomatik olarak araması için ayarlanmışsa yeni sürüm Güncelleştirmeler listesinde görünür.  

     Güncelleştirmeler bölmesinin alt kısmında güncelleştirmeler için  otomatik denetimi etkinleştirebilirsiniz veya devre dışı ekleyebilirsiniz ( Kullanılabilir güncelleştirmelerin otomatik algılanmasına olanak tanıyın/devre dışı bırak), bu ayar Araçlar  Seçenekleri Ortam Uzantıları ve Güncelleştirmeleri'nde Güncelleştirmeleri denetleme ayarını  >    >    >  **değiştirir.**

    > [!NOTE]
    > Visual Studio 2015 Güncelleştirme 2'den başlayarak, kullanıcı başına uzantılar, tüm kullanıcı uzantıları veya her ikisi (varsayılan ayar) için otomatik güncelleştirmeler isteyip istemeyebilirsiniz (Araçlar Seçenekler Ortam Uzantıları ve  >    >    >  Güncelleştirmeler'de) belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)
- [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md)

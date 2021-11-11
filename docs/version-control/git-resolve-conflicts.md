---
title: Visual Studio birleştirme çakışmalarını çözün
titleSuffix: ''
description: Visual Studio birleştirme çakışmalarını anlama, önlemek ve çözmek.
ms.date: 11/10/2021
ms.topic: how-to
author: Taysser-Gherfal
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: c088e526f4a999f0637068322c4a26f4900f3f81
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264035"
---
# <a name="resolve-merge-conflicts-in-visual-studio"></a>Visual Studio birleştirme çakışmalarını çözün

Bir dalı diğeriyle birleştirdiğinizde, bir daldaki işlemelerin dosya değişiklikleri diğer değişikliklerle çakışabilir. Git, birleştirilmiş dosyaların ne gibi görünmesi gerektiğini belirlemek üzere deponuzdaki geçmişi kullanarak bu değişiklikleri çözümlemeye çalışır. Değişiklikleri birleştirme hakkında net olmadığında, git 'in birleştirme işlemini durdurur ve hangi dosyaların çakıştığını söyler.

## <a name="understand-merge-conflicts"></a>Birleştirme çakışmalarını anlama

Aşağıdaki görüntüde değişikliklerin git 'te nasıl çakıştığını gösteren çok basit bir örnek gösterilmektedir. Hem Main hem de bugdüzeltmesini dalı, kaynak kodu için aynı satırlara güncelleştirmeler yapar.

:::image type="content" source="media/vs-2022/git-conflicts-understand-1.png" alt-text="Birleştirme çakışmasını gösteren diyagram.":::

Bugdüzeltmesini ana olarak birleştirmeye çalışırsanız, git birleştirilmiş sürümde hangi değişikliklerin kullanılacağını belirleyemez. Değişiklikleri ana dalda, bugdüzeltmesini dalında veya ikisinin bir birleşimi içinde tutmak isteyebilirsiniz. Bu çakışmayı, iki dal arasındaki çakışan değişiklikleri karşılayan ana dalda bir birleştirme işlemesiyle çözün.

:::image type="content" source="media/vs-2022/git-conflicts-understand-2.png" alt-text="Birleştirme işlemenin birleştirme çakışmasını nasıl çözdüğünü gösteren diyagram.":::

En yaygın birleştirme çakışması durumu, bir uzak daldan yerel dalınıza (örneğin, kaynak/bugdüzeltmesini yerel bugdüzeltmesini dalınıza) kadar güncelleştirmeleri çektiğinizde olur. Bu çakışmaları aynı şekilde çözümleyin-yerel dalınızda değişiklikleri mutabık kılma ve birleştirme işlemini tamamlamaya yönelik bir birleştirme yürütmesi oluşturun.

## <a name="prevent-merge-conflicts"></a>Birleştirme Çakışmalarını Önle

Dosya içerikleri işlemeler arasında önemli ölçüde değişmiyorsa, git pek çok durumda otomatik olarak dosya değişiklikleri birleştirme konusunda oldukça iyidir. Dalınızın ana dalınızın ötesinde bir çekme isteği açmadan önce dalları yeniden temellendirin. Yeniden temel dallar, çakışma olmadan ana dalınızla birleşir.

## <a name="resolve-merge-conflicts"></a>Birleştirme çakışmalarını çözümleme

- Aynı dalda başkalarıyla işbirliği yapıyorsanız, değişikliklerinizi gönderdiğinizde birleştirme çakışmalarını da alabilirsiniz.

    :::image type="content" source="media/vs-2022/git-conflicts-push-link.png" alt-text="Bir gönderden sonra birleştirme çakışması ekran görüntüsü.":::

- değişikliklerinizi gönderdiğinizde Visual Studio, üzerinde çalıştığınız yerel dalın kendi uzak izleme dalının gerisinde olup olmadığını algılar ve ardından, aralarından seçim yapabileceğiniz çeşitli seçenekler sunar.

    :::image type="content" source="media/vs-2022/git-conflicts-pull-push-ui.png" alt-text="Yerel dal uzak dalın arkasında olduğunda kullanılabilen seçeneklerin ekran görüntüsü.":::

    > [!NOTE]
    > uzak deponuz bunu, **Git > Ayarlar** aracılığıyla etkinleştirerek destekliyorsa, gönderimi zorla ' yı etkinleştirebilirsiniz.

- Bu, uzak depoya getirilen değişiklikleri dahil **etmek için göndermeyi** ve göndermeyi seçelim. değişiklikleri çekilirken veya iki dalı birleştirmeye çalışırken herhangi bir birleştirme çakışması varsa, Visual Studio git değişiklikleri penceresinde, git deposu penceresinde ve çakışmalar içeren tüm belgelerde bize bilgi verir.

    :::image type="content" source="media/vs-2022/git-conflicts-notification-ui.png" alt-text="Birleştirme çakışması bildiriminin ekran görüntüsü.":::

- **Git değişiklikleri** penceresinde, birleştirilmemiş değişiklikler altında çakışmalar bulunan belgelerin bir listesi gösterilir. Çakışmaları çözmeye başlamak için, çözümlemek istediğiniz belgeye çift tıklayabilirsiniz veya düzenleyicide açık çakışmalar içeren bir belgeniz varsa, birleştirme düzenleyicisini aç ' ı seçebilirsiniz.

    :::image type="content" source="media/vs-2022/git-conflicts-status-ui.png" alt-text="Git değişiklikleri penceresinde birleştirme çakışması durumunun ekran görüntüsü." lightbox="media/vs-2022/git-conflicts-status-ui.png":::

- **Birleştirme düzenleyicisini** açtıktan sonra, aşağıdaki yöntemlerden herhangi birini kullanarak (numaralandırılmış ekran görüntüsünde gösterildiği gibi) çakışmayı çözmeye başlayabilirsiniz.

    1. Çakışmalar satırını satıra göre ilerleyin ve onay kutularını işaretleyerek sağ veya sol tarafı tutarak seçin.
    1. Çakışan değişikliklerinizin tümünü tutun veya yoksayın.
    1. Kodunuzu, sonuç penceresinde el ile düzenleyin.

    :::image type="content" source="media/vs-2022/git-conflicts-resolve-conflict.png" alt-text="Visual Studio 2022 ' de birleştirme çakışmasını çözmeyi gösteren ekran görüntüsü." lightbox="media/vs-2022/git-conflicts-resolve-conflict.png":::

    > [!TIP]
    > Birleştirme Düzenleyicisi varsayılan yerleşimini beğenmezseniz, dişli açılan menüsünü kullanarak bunu değiştirebilirsiniz.
    >
    > :::image type="content" source="media/vs-2022/git-conflicts-layout-options.png" alt-text="Birleştirme Düzenleyicisi Düzen seçeneklerinin ekran görüntüsü.":::
    >
    >Örneğin, aşağıdaki ekran görüntüsünde dikey görünümün nasıl göründüğü gösterilmektedir:
    >
    > :::image type="content" source="media/vs-2022/git-conflicts-vertical-view.png" alt-text="Birleştirme Düzenleyicisi Kullanıcı arabirimindeki dikey görünümün ekran görüntüsü." lightbox="media/vs-2022/git-conflicts-vertical-view.png":::

- Birleştirme çakışmalarını çözmeyi tamamladığınızda **birleştirmeyi kabul et**' i seçin. Çakışan tüm dosyalar için bunu tekrarlayın.

    :::image type="content" source="media/vs-2022/git-conflicts-accept-merge.png" alt-text="Visual Studio 2022 ' de birleştirme eylemini kabul etme ekranının ekran görüntüsü.":::

- **Git değişiklikleri** penceresini kullanarak bir birleştirme yürütmesi oluşturun ve çakışmayı çözün.

    :::image type="content" source="media/vs-2022/git-conflicts-merge-commit.png" alt-text="Git değişiklikleri penceresini kullanarak birleştirme yürütmesinin nasıl oluşturulacağı ekran görüntüsü.":::

    > [!NOTE]
    > Bir belgede yaptığınız tüm değişiklikleri tutmanız gerekiyorsa, bu öğeyi **Birleştirilmemiş değişiklikler** bölümünde sağ tıklayıp, birleştirme düzenleyicisini açmak zorunda kalmadan **geçerli (yerel) tut** seçeneğini belirleyebilirsiniz.
    >
    > :::image type="content" source="media/vs-2022/git-conflicts-keep-changes.png" alt-text="' Geçerli tut ve geleni Al menü seçeneklerinin ekran görüntüsü.":::

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğa devam etmek için aşağıdaki bağlantıyı kullanarak birleştirme ve birleştirme çakışmalarını [Git birleştirme ve çakışmaları çözme](https://git-scm.com/docs/git-merge)hakkında daha fazla bilgi edinin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio git deneyimi](../ide/git-with-visual-studio.md)
- [Visual Studio & GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
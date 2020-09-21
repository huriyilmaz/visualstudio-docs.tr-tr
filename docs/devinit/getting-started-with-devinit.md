---
title: Devinit ile çalışmaya başlama
description: Devınit için Başlarken Kılavuzu.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: e0c6676b65637840a1b5878e06d6c5861c34e65d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809315"
---
# <a name="getting-started-with-devinit"></a>Devinit ile çalışmaya başlama

## <a name="step-1-get-devinit"></a>1. Adım: devinit al

devinit Şu anda yalnızca Visual Studio kullanılırken GitHub Codespaces 'ın bir parçası olarak kullanılabilir ve Visual Studio 'daki tümleşik terminalden erişilebilir. Daha sonra devinit, Visual Studio 'nun bir parçası olarak kullanılabilir olacaktır.

## <a name="step-2-define-your-environment"></a>2. Adım: ortamınızı tanımlama

En önemli adım, ' Geliştirici ' ortamınızı dosyadaki bir [ _.devinit.js_ ](devinit-json.md)tanımlamaktır. Bu dosya, çalıştırdığınızda ortamınızı oluşturmak için devinit tarafından kullanılacaktır `devinit init` .

Bu adım için, bir projeyi bir proje deposu ile çalışmaya ve çalıştırmaya verdiğiniz yönergeleri düşünün. Örneğin, SQL 'in yüklü olması gerekir mi? .NET Core 'un belirli bir sürümü mi? benzerlerini. Ardından, bu bağımlılıkların her biri için, [Araçlar listesinde](devinit-tool-list.md)karşılık gelen bir devinit aracını arayın ve bu dosyayı deponun _.devinit.js_ dosyasına ekleyin.

## <a name="step-3-enjoy"></a>3. Adım: keyfini çıkarın!

Şimdi, deponuzu kopyaladıktan sonra tüm birisinin yapması gerekiyor `devinit init` .

```batch
> devinit init
```

[GitHub Codespaces](https://github.com/features/codespaces)kullanıyorsanız, `devinit init` codespace sağlandığında otomatik olarak çalışacak şekilde yapılandırabilirsiniz. Daha fazla bilgi edinmek için [devinit ve GitHub Codespaces belgelerine](devinit-and-codespaces.md)göz atın.

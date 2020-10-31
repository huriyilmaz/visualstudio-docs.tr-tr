---
title: Devinit ile çalışmaya başlama
description: Devınit için Başlarken Kılavuzu.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ae274e460f4404efa92c4cf3785a3c2e41fd9691
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134079"
---
# <a name="getting-started-with-devinit"></a>Devinit ile çalışmaya başlama

## <a name="step-1-get-devinit"></a>1. Adım: devinit al

devinit Şu anda yalnızca Visual Studio kullanılırken GitHub Codespaces 'ın bir parçası olarak kullanılabilir ve Visual Studio 'daki tümleşik terminalden erişilebilir. Daha sonra devinit, Visual Studio 'nun bir parçası olarak kullanılabilir olacaktır.

## <a name="step-2-define-your-environment"></a>2. Adım: ortamınızı tanımlama

En önemli adım, ' Geliştirici ' ortamınızı dosyadaki bir [ _.devinit.js_](devinit-json.md)tanımlamaktır. Bu dosya, çalıştırdığınızda ortamınızı oluşturmak için devinit tarafından kullanılacaktır `devinit init` .

Bu adım için, bir projeyi bir proje deposu ile çalışmaya ve çalıştırmaya verdiğiniz yönergeleri düşünün. Örneğin, SQL 'in yüklü olması gerekir mi? .NET Core 'un belirli bir sürümü mi? benzerlerini. Ardından, bu bağımlılıkların her biri için, [Araçlar listesinde](devinit-tool-list.md) ilgili bir devinit aracını arayın ve dosyayı depodaki _.devinit.js_ dosyasına ekleyin.

## <a name="step-3-enjoy"></a>3. Adım: keyfini çıkarın!

Şimdi, deponuzu kopyaladıktan sonra tüm birisinin yapması gerekiyor `devinit init` .

```console
devinit init
```

[GitHub Codespaces](https://github.com/features/codespaces)kullanıyorsanız, `devinit init` codespace sağlandığında otomatik olarak çalışacak şekilde yapılandırabilirsiniz. Daha fazla bilgi edinmek için [devinit ve GitHub Codespaces belgelerine](devinit-and-codespaces.md)göz atın.

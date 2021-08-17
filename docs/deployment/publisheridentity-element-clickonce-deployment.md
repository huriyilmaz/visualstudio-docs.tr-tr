---
title: '&lt;publisherIdentity &gt; Öğesi (ClickOnce Dağıtımı) | Microsoft Docs'
description: publisherIdentity öğesi, bir dağıtım bildirimini imzalayan yayımcı hakkında bilgiler içerir. öğesi imzalı bildirimlerde gereklidir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: a0421172d9f97fde3fcf558214b7325152e3c15373a70d242f9b68c013a5cc42
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343423"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity &gt; öğesi (ClickOnce dağıtım)
Bu dağıtım bildirimini imzalayan yayımcı hakkında bilgi içerir.

## <a name="syntax"></a>Syntax

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 öğesi `publisherIdentity` imzalı bildirimlerde gereklidir. Aşağıdaki tabloda, öğesinin desteklediği `publisherIdentity` öznitelikler gösterir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Bu uygulamayı yayımladığı taraf kimliğini açıklar.|
|`issuerKeyHash`|Gereklidir. Sertifikayı içeren ortak anahtarın SHA-1 karması içerir.|

#### <a name="parameters"></a>Parametreler

## <a name="property-valuereturn-value"></a>Özellik değeri/dönüş değeri

## <a name="exceptions"></a>Özel durumlar

## <a name="remarks"></a>Açıklamalar

## <a name="requirements"></a>Gereksinimler

## <a name="subhead"></a>Alt başlık
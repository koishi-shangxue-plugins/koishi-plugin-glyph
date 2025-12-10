
# API

## `ctx.glyph` 服务

### `getFontDataUrl(name: string): string | null`

获取指定字体的 Base64 Data URL。

- **参数**：`name` - 字体名称（不含扩展名）
- **返回**：字体的 Data URL，如果字体不存在则返回 `null`

```typescript
const fontDataUrl = ctx.glyph.getFontDataUrl('NotoColorEmoji-Regular');
// 返回: 'data:font/truetype;charset=utf-8;base64,AAABAAIAA...'
```

### `getFontNames(): string[]`

获取所有已加载的字体名称列表。

```typescript
const fonts = ctx.glyph.getFontNames();
// 返回: ['NotoColorEmoji-Regular', 'MiSans-Regular', ...]
```

### `getFontInfo(name: string): FontInfo | undefined`

获取字体的详细信息（名称、格式、大小等）。

```typescript
const info = ctx.glyph.getFontInfo('NotoColorEmoji-Regular');
// 返回: { name: 'NotoColorEmoji-Regular', format: 'truetype', size: 1234567, ... }
```

### `checkFont(fontName: string, downloadUrl: string): Promise<boolean>`

检查字体是否存在，如果不存在则从指定 URL 下载。

- **参数**：
  - `fontName` - 字体名称（不含扩展名）
  - `downloadUrl` - 字体文件的下载 URL
- **返回**：`true` 表示字体可用，`false` 表示下载失败

```typescript
const success = await ctx.glyph.checkFont(
  'NotoColorEmoji-Regular',
  'https://cdn.jsdelivr.net/gh/googlefonts/noto-emoji@main/fonts/NotoColorEmoji.ttf'
);
```

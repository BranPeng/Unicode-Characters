# Unicode-Characters

```
public extension UILabel {

func addBulletPoint(stringList: [String],
font: UIFont,
bullet: String = "\u{2022}",
indentation: CGFloat = 20,
lineSpacing: CGFloat = 2,
paragraphSpacing: CGFloat = 10,
textColor: UIColor = .gray,
bulletColor: UIColor = .gray) -> NSAttributedString {

let textAttributes: [NSAttributedString.Key: Any] = [NSAttributedString.Key.font: font, NSAttributedString.Key.foregroundColor: textColor]
let bulletAttributes: [NSAttributedString.Key: Any] = [NSAttributedString.Key.font: font, NSAttributedString.Key.foregroundColor: bulletColor]

let paragraphStyle = NSMutableParagraphStyle()
let nonOptions = [NSTextTab.OptionKey: Any]()
paragraphStyle.tabStops = [
NSTextTab(textAlignment: .left, location: indentation, options: nonOptions)]
paragraphStyle.defaultTabInterval = indentation
paragraphStyle.lineSpacing = lineSpacing
paragraphStyle.paragraphSpacing = paragraphSpacing
paragraphStyle.headIndent = indentation

let bulletList = NSMutableAttributedString()
for string in stringList {
let formattedString = "\(bullet)\t\(string)\n"
let attributedString = NSMutableAttributedString(string: formattedString)

attributedString.addAttributes(
[NSAttributedString.Key.paragraphStyle : paragraphStyle],
range: NSMakeRange(0, attributedString.length))

attributedString.addAttributes(
textAttributes,
range: NSMakeRange(0, attributedString.length))

let string:NSString = NSString(string: formattedString)
let rangeForBullet:NSRange = string.range(of: bullet)
attributedString.addAttributes(bulletAttributes, range: rangeForBullet)
bulletList.append(attributedString)
}

return bulletList
}

}

```

```
self.bulletpointsLbl.attributedText = self.bulletpointsLbl.addBulletPoint(stringList: bulletString, font: UIFont.systemFont(ofSize: 14.0), bullet: "\u{2022}", indentation: 20, lineSpacing: 2, paragraphSpacing: 10, textColor: Utils.colorWithHexString(hexString: "606060"), bulletColor: Utils.colorWithHexString(hexString: "79bf49"))
```

[Unicode Character Category 'Symbol, Other'](http://www.fileformat.info/info/unicode/category/So/index.htm)

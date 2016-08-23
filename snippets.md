# Code Snippets


* `var ninjaAttackAnimation = SKAction()`

		if location.x < ninja?.position.x  && ninja?.xScale > 0 {
			ninja?.xScale *= -1.0
		}

		if location.x > ninja?.position.x && ninja?.xScale < 0 {
			ninja?.xScale *= -1.0
		}




	let attackAction = SKAction.sequence([ninjaAttackAnimation, ninjaWalkAnimation])
	ninja?.runAction(attackAction)




	//ninja attack animation
	let ninjaAttackAtlas = SKTextureAtlas(named: "NinjaAttack")
	var ninjaAttackArray = [SKTexture]()
	for textureName in ninjaAttackAtlas.textureNames.sort() {
	ninjaAttackArray.append(ninjaAttackAtlas.textureNamed(textureName))
	}
	ninjaAttackAnimation = SKAction.animateWithTextures(ninjaAttackArray, timePerFrame: 1.0/24.0, resize: true, restore: true)
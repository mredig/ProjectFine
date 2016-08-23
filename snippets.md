# Code Snippets


variable declaration


		var ninjaAttackAnimation = SKAction()


flip ninja when going left

		if location.x < ninja?.position.x  && ninja?.xScale > 0 {
			ninja?.xScale *= -1.0
		}

		if location.x > ninja?.position.x && ninja?.xScale < 0 {
			ninja?.xScale *= -1.0
		}




run animation for ninja attack

		let attackAction = SKAction.sequence([ninjaAttackAnimation, ninjaWalkAnimation])
		ninja?.runAction(attackAction)



create ninja attack animation

		//ninja attack animation
		let ninjaAttackAtlas = SKTextureAtlas(named: "NinjaAttack")
		var ninjaAttackArray = [SKTexture]()
		for textureName in ninjaAttackAtlas.textureNames.sort() {
		ninjaAttackArray.append(ninjaAttackAtlas.textureNamed(textureName))
		}
		ninjaAttackAnimation = SKAction.animateWithTextures(ninjaAttackArray, timePerFrame: 1.0/24.0, resize: true, restore: true)
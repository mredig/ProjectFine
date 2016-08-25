# Code Snippets


Class variables

		let ogreCooldownTime:NSTimeInterval = 2.0
		var ogreLastAttack:NSTimeInterval = 0.0




Goes inside update


		let isClose = distanceBetweenIsWithinXDistance(ogre.position, ninja.position, 3)

		if ninja.position.x <= ogre.position.x && !isClose {
			ogre.xScale = -1
		} else {
			ogre.xScale = 1
		}


		let timeSinceLastAttack = currentTime - ogreLastAttack
		if distanceBetweenIsWithinXDistance(ogre.position, ninja.position, 64.0) && timeSinceLastAttack > ogreCooldownTime {
		//ogre attack!
			ogre.runAction(ogreAttackAnimation)
			ogreLastAttack = currentTime
		}







### Old Code


variable declaration

		var ogreDieAnimation = SKAction()


create animation



		//ogre die animation
		let ogreDieAtlas = SKTextureAtlas(named: "OgreDie")
		var ogreDieArray = [SKTexture]()
		for textureName in ogreDieAtlas.textureNames.sort() {
			ogreDieArray.append(ogreDieAtlas.textureNamed(textureName))
		}
		ogreDieAnimation = SKAction.animateWithTextures(ogreDieArray, timePerFrame: 1.0/24.0, resize: true, restore: true)




run ogre action


		let randomizeOgreAction = SKAction.customActionWithDuration(0, actionBlock: { (SKNode, CGFloat) in
			self.randomizeOgrePosition()
		})

		let ogreDieAction = SKAction.sequence([ogreDieAnimation, randomizeOgreAction])
		let ogre = self.childNodeWithName("Ralph The Ogre")

		ogre?.runAction(ogreDieAction)







### OLD STUFF


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
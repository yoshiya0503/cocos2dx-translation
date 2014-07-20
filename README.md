cocos2dx-translation
====================

this is translation to cocos2dx v-3.0 from cocos2dx v-2.0

Director
======
v2.0
    
    CCDirector* director = CCDirector::sharedDirector();

v3.0
    
    // sharedXXXX to getInstance(), this is singleton
    auto director = Director::getInstance();


Point
======
v2.0
    
    CCP p = ccp(1024, 1024);

v3.0
    
    // ccp to Point
    auto p = Point(1024, 1024);


Touch Event
======
v2.0
    
    class GameScene : public Layer {
    public:
        virtual bool ccTouchBegan(cocos2d::CCTouch*, cocos2d::CCEvent*);
        virtual void ccTouchEnded(cocos2d::CCTouch*, cocos2d::CCEvent*)
    };

    bool GameScene::ccTouchBegan(CCTouch* pt, CCEvent pe) {
        return true; 
    }

    void GameScene::ccTouchEnded(CCTouch* pt, CCEvent pe) {
        return;
    }

v3.0

    class GameScene : public Layer {
    public:
        // remove CC prefix
        virtual bool TouchBegan(cocos2d::Touch*, cocos2d::Event*);
        virtual void TouchEnded(cocos2d::Touch*, cocos2d::Event*)
    };

    bool GameScene::TouchBegan(Touch* pt, Event pe) {
        return true; 
    }

    void GameScene::TouchEnded(Touch* pt, Event pe) {
        return;
    }


Schedule
=======
v2.0

    class GameScene : public layer {
    public:
        void test();
        void measure();
    };
    
    void GameScene::test() {
        this->schedule(schedule_selector(GameScene::measure));    
    }

    void GameScene::measure() {
        return;
    }

v3.0

    class GameScene : public layer {
    public:
        void test();
        void measure();
    };
    
    void GameScene::test() {
        this->schedule(schedule_selector(GameScene::measure));    
    }

    // need float type arg
    void GameScene::measure(float time) {
        return;
    }


Label
=======
v2.0

    class GameScene : public layer {
    public:
        void test();
    };

    void GameScene::test() {
        CCLabelTTF* timerLabel = (CCLabelTTF*)this->getChildByTag(tag);
    }

v3.0

    class GameScene : public layer {
    public:
        void test();
    };

    void GameScene::test() {
        // remove CC and TTF
        auto timerLabel = (Label*)this->getChildByTag(tag);
    }


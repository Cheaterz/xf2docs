# Basic example
```
<h2 class="block-tabHeader block-tabHeader--memberTabs tabs hScroller"
            data-xf-init="tabs h-scroller"
            data-panes=".js-memberTabPanes"
            data-state="replace"
            role="tablist">
            <span class="hScroller-scroll">
                <!--[XF:tabs:start]-->
                    <a href="#"
                        class="tabs-tab is-active"
                        role="tab"
                        aria-controls="profile-posts">{{ phrase('profile_posts') }}</a>
                
                    <a href="#"
                        rel="nofollow"
                        class="tabs-tab"
                        id="latest-activity"
                        role="tab">{{ phrase('latest_activity') }}</a>
                
                <a href="#"
                    rel="nofollow"
                    class="tabs-tab"
                    id="recent-content"
                    role="tab">{{ phrase('postings') }}</a>

                <!--[XF:tabs:after_recent_content]-->

                <a href="#"
                    class="tabs-tab"
                    id="about"
                    role="tab">{{ phrase('about') }}</a>

                    <a href="#"
                        class="tabs-tab"
                        id="warnings"
                        role="tab">{{ phrase('warnings') }}</a>
                <!--[XF:tabs:end]-->
            </span>
        </h2>
```

And the contents:
```
<ul class="tabPanes js-memberTabPanes">
    <!--[XF:tab_panes:start]-->
        <li class="is-active" role="tabpanel" id="profile-posts">
            <xf:js src="xf/inline_mod.js" min="1" />
            <div class="block block--messages" data-xf-init="inline-mod" data-type="profile_post" data-href="{{ link('inline-mod') }}">
                <div class="block-container">
                    <div class="block-body js-replyNewMessageContainer">
                            
                        <!--[XF:
                        <xf:if is="$profilePosts is not empty">
                            <xf:foreach loop="$profilePosts" value="$profilePost">
                                <xf:macro template="profile_post_macros"
                                    name="{{ $profilePost.message_state == 'deleted' ? 'profile_post_deleted' : 'profile_post' }}"
                                    arg-profilePost="{$profilePost}" />
                            </xf:foreach>
                        <xf:else />
                            <div class="block-row js-replyNoMessages">{{ phrase('there_no_messages_on_xs_profile_yet', {'name': "fdsdgfd"}) }}</div>
                        </xf:if>
                        ]-->
                    </div>
                </div>

                <div class="block-outer block-outer--after">
                    <xf:comment><!-- <xf:pagenav
                        page="{$page}" perpage="{$perPage}" total="{$total}"
                        link="members" data="{$user}"
                        wrapperclass="block-outer-main" /> --></xf:comment>
                    <div class="block-outer-opposite">
                        <xf:comment><!-- <xf:macro template="inline_mod_macros" name="button" /> --></xf:comment>
                    </div>
                </div>
            </div>
        </li>

        <li data-href="{{ link('members/recent-content', $user) }}" role="tabpanel" aria-labelledby="latest-activity">
            <div class="blockMessage">{{ phrase('loading...') }}</div>
        </li>

    <li data-href="#" role="tabpanel" aria-labelledby="recent-content">
        <div class="blockMessage">{{ phrase('loading...') }}</div>
    </li>

    <!--[XF:tab_panes:after_recent_content]-->

    <li data-href="#" role="tabpanel" aria-labelledby="about">
        <div class="blockMessage">{{ phrase('loading...') }}</div>
    </li>

        <li data-href="#" role="tabpanel" aria-labelledby="warnings">
            <div class="blockMessage">{{ phrase('loading...') }}</div>
        </li>
    <!--[XF:tab_panes:end]-->
</ul>
```

**WARNING!** Tabs and panes count *MUST* be equal.
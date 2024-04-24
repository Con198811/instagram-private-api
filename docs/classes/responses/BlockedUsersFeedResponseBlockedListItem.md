[instagram-private-api](../../README.md) / [responses](../../modules/responses.md) / BlockedUsersFeedResponseBlockedListItem

# Class: BlockedUsersFeedResponseBlockedListItem

[responses](../../modules/responses.md).BlockedUsersFeedResponseBlockedListItem

## Hierarchy

- [`Entity`](../index/Entity.md)

  ↳ **`BlockedUsersFeedResponseBlockedListItem`**

## Table of contents

import { Expose, plainToClassFromExist } from 'class-transformer';
import { Feed } from '../core/feed';
import { BlockedUsersFeedResponseRootObject, BlockedUsersFeedResponseBlockedListItem } from '../responses';

export class BlockedUsersFeed extends Feed<
  BlockedUsersFeedResponseRootObject,### profile\_pic\_url

• **profile\_pic\_url**: `string`

#### Defined in
  BlockedUsersFeedResponseBlockedListItem
> {
  @Expose()
  private nextMaxId: string;

  set state(body: BlockedUsersFeedResponseRootObject) {
    this.moreAvailable = !!body.next_max_id;
    this.nextMaxId = body.next_max_id;
  }

  async request() {
    const { body } = await this.client.request.send<BlockedUsersFeedResponseRootObject>({
      url: `/api/v1/users/blocked_list/`,
      qs: {
        max_id: this.nextMaxId,
      },
    });
    this.state = body;
    return body;
  }

  async items() {
    const body = await this.request();
    return body.blocked_list.map(user =>
      plainToClassFromExist(new BlockedUsersFeedResponseBlockedListItem(this.client), user),
    );
  }
}

### Constructors

- [constructor](BlockedUsersFeedResponseBlockedListItem.md#constructor)

### Properties

- [block\_at](BlockedUsersFeedResponseBlockedListItem.md#block_at)
- [full\_name](BlockedUsersFeedResponseBlockedListItem.md#full_name)
- [profile\_pic\_url](BlockedUsersFeedResponseBlockedListItem.md#profile_pic_url)
- [user\_id](BlockedUsersFeedResponseBlockedListItem.md#user_id)
- [username](BlockedUsersFeedResponseBlockedListItem.md#username)

## Constructors

### constructor

• **new BlockedUsersFeedResponseBlockedListItem**(`client`)

#### Parameters

| Name | Type |
| :------ | :------ |
| `client` | [`IgApiClient`](../index/IgApiClient.md) |

#### Inherited from

[Entity](../index/Entity.md).[constructor](../index/Entity.md#constructor)

#### Defined in

[src/core/repository.ts:7](https://github.com/Nerixyz/instagram-private-api/blob/b3351b9/src/core/repository.ts#L7)

## Properties

### block\_at

• **block\_at**: `number`

#### Defined in

[src/responses/blocked-users.feed.response.ts:14](https://github.com/Nerixyz/instagram-private-api/blob/b3351b9/src/responses/blocked-users.feed.response.ts#L14)

___

### full\_name

• **full\_name**: `string`

#### Defined in

[src/responses/blocked-users.feed.response.ts:12](https://github.com/Nerixyz/instagram-private-api/blob/b3351b9/src/responses/blocked-users.feed.response.ts#L12)

___



[src/responses/blocked-users.feed.response.ts:13](https://github.com/Nerixyz/instagram-private-api/blob/b3351b9/src/responses/blocked-users.feed.response.ts#L13)

___

### user\_id

• **user\_id**: `number`

#### Defined in

[src/responses/blocked-users.feed.response.ts:10](https://github.com/Nerixyz/instagram-private-api/blob/b3351b9/src/responses/blocked-users.feed.response.ts#L10)

___

### username

• **username**: `string`

#### Defined in

[src/responses/blocked-users.feed.response.ts:11](https://github.com/Nerixyz/instagram-private-api/blob/b3351b9/src/responses/blocked-users.feed.response.ts#L11)

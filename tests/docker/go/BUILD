# Copyright 2017 The Bazel Authors. All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
package(default_visibility = ["//visibility:public"])

load("//go:image.bzl", "go_image")
load("//contrib:test.bzl", "container_test")

go_image(
    name = "go_image",
    srcs = ["//testdata:main.go"],
    args = [
        "arg0",
        "arg1",
        "$(location :BUILD)",
    ],
    data = [":BUILD"],
    importpath = "github.com/bazelbuild/rules_docker/docker/tests/docker/go",
    tags = [
        "tag1",
        "tag2",
    ],
)

container_test(
    name = "go_image_test",
    configs = ["//tests/docker/go/configs:go_image.yaml"],
    image = ":go_image",
)

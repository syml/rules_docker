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

load("//python:image.bzl", "py_image")
load("//contrib:test.bzl", "container_test")

py_library(
    name = "py_image_library",
    srcs = ["//testdata:py_image_library.py"],
)

py_image(
    name = "py_image",
    srcs = ["//testdata:py_image.py"],
    args = [
        "arg0",
        "arg1",
        "$(location :BUILD)",
    ],
    data = [":BUILD"],
    layers = [
        ":py_image_library",
    ],
)

container_test(
    name = "py_image_test",
    configs = ["//tests/docker/python/configs:py_image.yaml"],
    image = ":py_image",
)
